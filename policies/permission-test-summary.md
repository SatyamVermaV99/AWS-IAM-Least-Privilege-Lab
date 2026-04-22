# Permission Test Summary

## Test Identity

IAM User: `project-readonly-analyst-test`

## Attached Policy

Policy: `AmazonEC2ReadOnlyAccess`

## Purpose

The purpose of this test was to validate least-privilege access for a read-only analyst-style IAM user. The user should be able to view EC2-related resources but should not be able to modify, launch, stop, terminate, or change network access to resources.

## Allowed Actions

| Service | Action | Result | Reason |
|---|---|---|---|
| EC2 | `DescribeInstances` | Allowed | Read-only EC2 visibility |
| EC2 | `DescribeSecurityGroups` | Allowed | Read-only security group visibility |
| EC2 | `DescribeVolumes` | Allowed | Read-only storage visibility |

## Denied Actions

| Service | Action | Result | Reason |
|---|---|---|---|
| EC2 | `StartInstances` | Denied | User should not modify instance state |
| EC2 | `StopInstances` | Denied | User should not modify instance state |
| EC2 | `TerminateInstances` | Denied | High-risk destructive action |
| EC2 | `RunInstances` | Denied | User should not launch new resources |
| EC2 | `AuthorizeSecurityGroupIngress` | Denied | User should not change inbound network access |

## Conclusion

The IAM user had appropriate read-only access for analyst-style visibility. The user was denied higher-risk actions that could modify infrastructure, create resources, terminate systems, or change network exposure. This confirms the permission set followed least-privilege principles.
