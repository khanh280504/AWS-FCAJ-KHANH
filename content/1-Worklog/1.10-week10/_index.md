---
title: "Worklog Week 10"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

> [!IMPORTANT]
> ### Week 10 Goal
> Build a complete CI/CD pipeline on AWS that automates code commit, build, test, and production deployment with CodeCommit, CodeBuild, CodeDeploy, and CodePipeline.

### Detailed implementation plan:

| Day | Detailed work | Start date | Completion date | Resource |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Study DevOps on AWS, CodeCommit, CodeBuild, GitFlow, and AWS Developer Tools. | 22/06/2026 | 22/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Study CodeDeploy and CodePipeline, including In-place and Blue/Green deployment. | 23/06/2026 | 23/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | Create a CodeCommit repository, push code, write `buildspec.yml`, and run the first CodeBuild build. | 24/06/2026 | 24/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | Create a Source to Build to Deploy CodePipeline and configure Blue/Green deployment to an EC2 Auto Scaling Group. | 25/06/2026 | 25/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Compare AWS-native CI/CD with GitHub Actions, review the pipeline architecture, and publish **Worklog Week 10**. | 26/06/2026 | 26/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### Deliverables
> * [x] CI/CD pipeline that builds, tests, and deploys from branch `main`.
> * [x] Blue/Green deployment with zero downtime and rollback behavior.
> * [x] `buildspec.yml` running unit tests before deployment.
> * [x] Worklog Week 10 published successfully.
