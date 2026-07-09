---
title: "Workshop"
date: 2026-07-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

<div class="lms">

# WORKSHOP - Deploying an LMS System on AWS

This workshop provides step-by-step guidance for building **LMS-Management-System**, an online learning management system, on AWS with a highly available architecture. Users access the system through **CloudFlare** and **AWS Amplify** for the frontend. The backend runs on **EC2** behind an **Application Load Balancer** and **Auto Scaling Group**. Data is stored in **Amazon DocumentDB** (Multi-AZ), and the whole system is monitored with **CloudWatch**, **CloudTrail**, and alerts through **Amazon SNS**.

### Workshop contents

* **5.1** - [Introduction](5.1-gioi-thieu/)
* **5.2** - [Build the network infrastructure](5.2-ha-tang-mang/)
* **5.3** - [Deploy the backend](5.3-backend/)
* **5.4** - [Configure the domain and frontend](5.4-domain-frontend/)
* **5.5** - [Load balancing and Auto Scaling](5.5-loadbalancing-autoscaling/)
* **5.6** - [Monitor the System](5.6-giam-sat/)
* **5.7** - [Clean Up Resources](5.7-don-dep/)

</div>
