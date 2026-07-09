---
title: "Worklog Week 7"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

> [!IMPORTANT]
> ### Week 7 Goal
> Master AWS IAM fundamentals: Users, Groups, Roles, Policies, MFA, and the Least Privilege principle. Build a layered security strategy for the AWS account.

### Detailed implementation plan:

| Day | Detailed work | Start date | Completion date | Resource |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Study IAM overview, Users, Groups, Policies, and the difference between identity-based and resource-based policies. | 01/06/2026 | 01/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Study IAM Roles, Instance Profiles, AWS Organizations, and SCPs. | 02/06/2026 | 02/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | Create an IAM User, assign it to `Developers`, write an S3 read-only custom policy, and enable MFA. | 03/06/2026 | 03/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | Create an EC2 role with S3 write and DynamoDB read permission; verify identity with `aws sts get-caller-identity`. | 04/06/2026 | 04/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Review Security Hub, GuardDuty, IAM Credential Report, and publish **Worklog Week 7**. | 05/06/2026 | 05/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### Deliverables
> * [x] IAM permissions designed with User, Group, Role, and Custom Policy.
> * [x] MFA enabled for important IAM users.
> * [x] EC2 calls S3 and DynamoDB through an IAM Role, without local access keys.
> * [x] IAM Access Analyzer review completed.
> * [x] Worklog Week 7 published successfully.
