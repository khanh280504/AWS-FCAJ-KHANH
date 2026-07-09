---
title: "Event 3"
date: 2026-05-30
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# REFLECTION: HERA INTRODUCTION — VOICE AGENT WORKSHOP ON AWS
---

> [!IMPORTANT]
> ### 🎯 Workshop goal and overview
> **Workshop Hera** is a detailed hands-on guide for deploying a real-time **Bilingual Voice Agent** using **Amazon Bedrock AgentCore Runtime** and the **Amazon Nova 2 Sonic** audio model.

## 1. What are Voice AI and the Hera project?

### Event participation information
* **Format:** Online.
* **Participation platform:** Google Meet.
* **Attendance time:** 8:00 PM.

### Voice Agent

Voice Agent is an artificial intelligence (AI) service that operates through **real-time bidirectional audio streaming**.

Workflow:

1. The user speaks into a microphone.
2. Audio is streamed to the speech-to-speech model.
3. The model processes the input and generates a spoken response.
4. The response audio is played back in the browser.

The entire cycle happens with latency under **1 second**.

### Hera

Hera uses **Amazon Nova 2 Sonic**, a speech-to-speech model on **Amazon Bedrock**, deployed in the **ap-northeast-1 (Tokyo)** region.

Key capabilities:

* Real-time voice communication.
* Support for Tool Use.
* Ability to query **Amazon Bedrock Knowledge Base** within the same streaming flow.

---

## 2. Reasons for choosing the Tech Stack

Workshop Hera is built on a combination of the following technologies.

### Amazon Nova 2 Sonic

* Native AWS speech-to-speech model.
* Low latency from Vietnam.
* Charged by minutes of usage.
* Supports natural Tool Use with Bedrock Knowledge Base.

### Amazon Bedrock AgentCore Runtime

* Managed runtime.
* No need to configure VPC, ALB, or NAT Gateway.
* Supports ARM64.
* Secured through IMDSv2.
* Easy to debug and operate.

### Pipecat (v1.1.0)

Pipecat acts as the orchestrator for the voice pipeline.

Characteristics:

* Built-in integration with `AWSNovaSonicLLMService`.
* Automatically handles Nova Sonic's maximum stream limit of **8 minutes**.
* Manages the entire voice loop.

### S3 Vectors + Titan v2

Low-cost RAG solution:

* Around **0.10 USD/month** for small datasets.
* Significantly cheaper than OpenSearch Serverless (**200-400 USD/month**).

### Terraform + AWS CDK (Python)

Combined Infrastructure as Code:

| Tool | Role |
|---------|----------|
| Terraform | Manages Bedrock Knowledge Base |
| AWS CDK (Python) | Deploys AgentCore Runtime |

---

## 3. Overall architecture

The voice processing workflow happens as follows.

### Step 1. Connection request

The browser requests a **WebSocket URL (WSS)** signed with **AWS SigV4**, valid for around **300 seconds**, from the **Presigner Lambda**.

### Step 2. Connection

The browser connects to **AgentCore Runtime** (Pipecat container) through WebSocket and streams **16 kHz** audio.

### Step 3. Tool Use

AgentCore Runtime forwards audio to Nova 2 Sonic.

When Sonic detects a question that needs data lookup, it calls the tool:

```text
lookup_product
```

### Step 4. RAG Retrieval

AgentCore Runtime calls:

```text
bedrock-agent-runtime.retrieve
```

to query **Bedrock Knowledge Base**.

The Knowledge Base returns:

* Top 3 results
* From S3 Vectors

Then AgentCore Runtime sends the results back to Nova Sonic within the same streaming flow.

### Step 5. Response

Nova Sonic:

* Generates a spoken response at 24 kHz.
* Sends audio back to AgentCore Runtime.
* AgentCore Runtime streams it back to the browser.
* The browser plays the audio for the user.

> The total processing time for one end-to-end conversation turn is around **3 seconds**.

---

## 4. Deployment Region

Default region:

```text
ap-northeast-1 (Tokyo)
```

Reasons:

* Lowest latency to Vietnam.
* Full support for:
  * Amazon Nova 2 Sonic
  * AgentCore Runtime
  * Bedrock Knowledge Base
  * S3 Vectors

Other supported regions:

* `us-east-1`
* `us-west-2`
* `eu-north-1`

---

## 5. Prerequisites

### AWS Account

Required:

* AWS Account
* IAM User
* `AdministratorAccess` permission

> Use only for the workshop, do not use the Root account.

### Knowledge

Learners should have basic knowledge of:

* AWS Console
* IAM
* VPC
* Docker
* Terraform

### Required tools

* AWS CLI v2
* Terraform >= 1.9
* uv (Python package manager)
* Docker Desktop (supports Buildx Multi-Arch)
* jq
* Chrome / Firefox / Safari (supports HTTPS and microphone)

> The workshop uses **uv**, not `pip`.

### Cost

Estimate:

* **2-5 USD**
* For around **2 hours** of hands-on practice.

> After completing the workshop, run the **Cleanup** section to avoid ongoing resource costs.

---

## 6. Workshop conventions

### Source code

Source code is organized by **Phase** for easier tracking.

### Images

All screenshots include:

* Red frame
* Directional arrows
* Captions at important steps in the AWS Console

### Language

The workshop uses:

* Chatbot: **English** (Nova Sonic works best with English)
* Documentation: **Bilingual English - Vietnamese (vi/en)**

> The CI system checks the number of Vietnamese and English pages. The build will fail if the two languages are not synchronized.

---

## 7. Main Hands-on Content of Hera

According to the workshop documentation, Hera is not only an architecture introduction. It guides learners through deploying a real voice chatbot end-to-end on their own AWS account. The hands-on section is divided into several stages, moving from the data layer to a complete web interface.

### 3.1 Knowledge Base

Learners build a **Bedrock Knowledge Base** using **S3 Vectors** as the vector backend and **Titan Text Embeddings v2** for embeddings. The goal is to turn product data into retrievable chunks that can be used when users ask questions by voice.

The important design choice is cost optimization. Instead of using OpenSearch Serverless, which is more suitable for larger systems but expensive to keep running, S3 Vectors makes the workshop more practical for students and short hands-on sessions.

### 3.2 Pipecat Local

Before deploying to AWS, learners run the voice agent locally. Pipecat orchestrates the pipeline: receiving audio, sending it to Nova Sonic, handling tool use, and returning responses. Running locally first helps validate the agent logic, model configuration, and RAG flow before moving to managed runtime.

### 3.3 Deploy AgentCore

After local testing, the Pipecat container is built for multiple architectures and deployed to **Amazon Bedrock AgentCore Runtime**. This step moves the project from development into a real runtime environment where the agent can receive browser connections through WebSocket.

### 3.4 Web Widget

The workshop deploys a static web widget built with HTML, JavaScript, and CSS. The widget is served through **S3 + CloudFront**, records audio in the browser, and sends it to AgentCore Runtime. Because browsers cannot sign a WebSocket upgrade with SigV4 by themselves, the system uses a **Presigner Lambda** to provide a short-lived WSS URL.

### 3.5 Observability

The observability section helps monitor the deployed system. The workshop refers to CloudWatch dashboards, operational logs, and alarms for detecting runtime failures or unexpected cost. This matters because a real-time voice agent must not only run; it must also be observable when streaming, runtime, or retrieval problems occur.

---

## 8. Detailed Voice Loop Analysis

One conversation turn in Hera can be understood as the following flow:

1. The user clicks record on the widget and asks a question.
2. The browser records audio through AudioWorklet as 16 kHz Int16 mono.
3. The browser calls Presigner Lambda to request a SigV4-signed WebSocket URL.
4. Presigner Lambda returns a short-lived WSS URL, valid for around 300 seconds.
5. The browser connects to AgentCore Runtime through WebSocket.
6. AgentCore Runtime runs the Pipecat container and forwards audio to Amazon Nova 2 Sonic.
7. Nova Sonic processes audio in a speech-to-speech flow.
8. If the question requires data lookup, Sonic emits tool use.
9. The runtime calls Bedrock Knowledge Base through `bedrock-agent-runtime.retrieve`.
10. The Knowledge Base retrieves top chunks from S3 Vectors.
11. The runtime sends retrieved content back to Nova Sonic in the same streaming session.
12. Nova Sonic generates 24 kHz audio, the runtime streams it back to the browser, and the browser plays it for the user.

This flow shows that Hera combines several technical layers: frontend audio processing, SigV4 connection authentication, managed agent compute, speech-to-speech foundation model, RAG retrieval, and real-time audio playback. It is a clear example of building modern AI applications not only with a model, but with the cloud ecosystem around that model.

---

## 9. Cost, Cleanup, and Operations

One part I appreciated in the workshop is that cost and cleanup are emphasized from the beginning. The documentation estimates around **2-5 USD** for a short hands-on session if resources are cleaned up properly. However, without cleanup, costs can continue from AgentCore Runtime, Bedrock Knowledge Base, CloudFront requests, or related resources.

### Why cleanup matters

In cloud workshops, learners often focus on successful deployment and forget to remove resources afterward. In Hera, cleanup is not only about manually deleting a few services. It also requires verifying that billable resources have actually stopped or been removed. The documentation mentions cleanup verification to reduce the risk of leftover resources.

### Observability in practice

Hera also emphasizes that a production-ready voice agent needs observability. Important signals include:

* WebSocket connection state.
* Runtime or container errors.
* Response time for a conversation turn.
* Knowledge Base retrieval failures.
* Bedrock and AgentCore usage cost.
* Alarms when cost exceeds expectations.

This helped me understand that deploying AI is not just about creating a working demo. A real AI system needs monitoring, logging, alerts, and a clear operational process.

---

## 10. Possible Extensions After the Workshop

From the workshop summary, Hera has several natural extension directions:

### Voice channel through Twilio

Instead of only talking through a browser, the system can be extended to phone calls using Twilio Media Streams. This would require additional audio conversion, because phone audio often uses 8 kHz audio while Sonic needs a stream suitable for voice-agent processing.

### Multilingual chatbot

The workshop currently prioritizes English because Nova Sonic performs best in English. A natural extension is automatic language detection and Vietnamese voice responses when model quality becomes strong enough.

### Multi-agent routing

Hera can evolve into a multi-agent system where an orchestrator routes questions to specialized agents such as sales, support, or billing. This pattern is useful for enterprise scenarios because each agent can own a separate knowledge domain.

### Persistent conversation history

The workshop version focuses mainly on the current voice loop. To support returning users, the system could add DynamoDB for session history, TTL for automatic expiration, and Cognito for user identity.

### Security and guardrails

When deployed with real data, the system should include guardrails for sensitive information, agent behavior control, and scope limitation. This is an important step when moving from a workshop demo to a real product environment.

---

> [!TIP]
> ### 💡 Lessons and general awareness (Synthesis)
>
> Through studying and practicing Workshop Hera, I gained several important technology insights:
>
> 1. **The revolution of real-time Voice AI**:
>    * Thanks to **Amazon Nova 2 Sonic** with an improved speech-to-speech architecture, two-way communication with AI no longer needs to be split into intermediate steps (STT -> LLM -> TTS). This optimizes latency to under 1 second and provides a natural conversation experience close to speaking with a real person.
> 2. **Optimizing infrastructure design and cost (Serverless and simplified RAG)**:
>    * Instead of using expensive OpenSearch Serverless (200-400 USD/month), the integrated **S3 Vectors + Titan v2** solution costs around 0.10 USD/month while still supporting RAG workloads well.
>    * Using **Amazon Bedrock AgentCore Runtime** simplifies the lifecycle management of Pipecat containers without complex VPC, ALB, or NAT Gateway configuration, reducing operational cost while maintaining security.
> 3. **The importance of synchronization in Infrastructure as Code (IaC)**:
>    * Combining **Terraform** (for Bedrock Knowledge Base) and **AWS CDK Python** (for AgentCore Runtime) creates a smooth deployment flow that is easy to manage and easy to clean up after the project ends.
