# AWS IAM Least-Privilege Testing Lab

## Project Description

This project is a hands-on AWS cloud security lab focused on IAM permission testing and least-privilege access control. The goal of this project was to create a controlled test IAM user, assign limited read-only permissions, validate allowed and denied actions using IAM Policy Simulator, and document the results in a professional security report.

The project demonstrates how an analyst can review IAM permissions, confirm whether access is appropriate, and identify whether a user has more permissions than required. It was completed fully through the AWS Management Console without deploying cloud infrastructure.

## Why I Created This Project

I created this project to build practical cloud security experience for entry-level cybersecurity analyst, SOC analyst, cloud security, and IAM analyst roles.

Many cybersecurity roles require an understanding of access control, least privilege, user permissions, and security documentation. This project helped me practice those skills in a safe AWS lab environment by testing a read-only analyst-style IAM user and confirming that higher-risk actions were denied.

## Tools Used

- AWS Identity and Access Management (IAM)
- AWS Managed Policies
- AmazonEC2ReadOnlyAccess policy
- IAM Policy Simulator
- AWS Management Console
- Markdown reporting
- Screenshot documentation

## Skills Demonstrated

- AWS IAM permission review
- Least-privilege access testing
- IAM policy analysis
- Allowed/denied action validation
- Cloud security documentation
- Access control review
- Security risk reduction
- Secure cleanup of test identities
- Analyst-style reporting

## Lab Scenario

A test IAM user was created to represent a read-only analyst account. The user was assigned the AWS managed policy `AmazonEC2ReadOnlyAccess`.

The policy was reviewed to understand the services and access levels granted to the user. IAM Policy Simulator was then used to test whether the user could perform safe read-only EC2 actions and whether higher-risk administrative actions were denied.

After testing was completed, the test IAM user was deleted to avoid leaving unused identities in the AWS account.

## Test Identity

| Field | Value |
|---|---|
| IAM User | `project-readonly-analyst-test` |
| Console Access | Disabled |
| Access Keys | Not created |
| Attached Policy | `AmazonEC2ReadOnlyAccess` |
| Policy Type | AWS Managed Policy |
| Project Focus | Least-privilege permission testing |

## Permission Testing Summary

### Allowed Read-Only Actions

The following actions were tested and allowed:

| Service | Action | Result |
|---|---|---|
| Amazon EC2 | `DescribeInstances` | Allowed |
| Amazon EC2 | `DescribeSecurityGroups` | Allowed |
| Amazon EC2 | `DescribeVolumes` | Allowed |

These actions are appropriate for a read-only analyst role because they provide visibility into EC2 resources without allowing changes.

### Denied Higher-Risk Actions

The following actions were tested and denied:

| Service | Action | Result |
|---|---|---|
| Amazon EC2 | `StartInstances` | Denied |
| Amazon EC2 | `StopInstances` | Denied |
| Amazon EC2 | `TerminateInstances` | Denied |
| Amazon EC2 | `RunInstances` | Denied |
| Amazon EC2 | `AuthorizeSecurityGroupIngress` | Denied |

These actions were denied because they could modify infrastructure, launch resources, terminate instances, or change network exposure.

## Key Findings

- The IAM test user was successfully created for controlled permission testing.
- Console access was disabled and no access keys were created, reducing unnecessary access risk.
- The `AmazonEC2ReadOnlyAccess` policy provided read-only visibility into EC2-related resources.
- IAM Policy Simulator confirmed that EC2 read-only actions were allowed.
- IAM Policy Simulator confirmed that higher-risk EC2 administrative actions were denied.
- The permission set followed least-privilege principles for a read-only analyst-style user.
- The test IAM user was deleted after testing to avoid leaving unused identities in the AWS account.

## Repository Structure

```text
aws-iam-least-privilege-lab/
│
├── README.md
│
├── reports/
│   └── iam-least-privilege-testing-report.md
│
├── screenshots/
│   ├── iam-user-created.png
│   ├── policy-attached.png
│   ├── policy-permissions-summary.png
│   ├── policy-simulator-allowed.png
│   ├── policy-simulator-denied.png
│   └── cleanup-user-deleted.png
│
└── policies/
    └── permission-test-summary.md
