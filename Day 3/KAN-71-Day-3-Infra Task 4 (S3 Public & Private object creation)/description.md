# KAN-71: Day-3-Infra Task 4 (S3 Public & Private object creation)

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-71
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-13T10:37:47.565Z
- **Updated:** 2026-10-14T04:26:31.553Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

AWS S3 Bucket Creation & Public/Private Object Access 

Today’s task focuses on creating an S3 bucket, uploading one public object and one private object, and configuring permissions so that the public object can be viewed by anyone while the private object can be viewed only by authorized team members.

Today’s Toolkit

1. S3 Bucket Creation - Create an S3 bucket with a unique name and keep Block Public Access enabled initially.
1. Object Upload - Upload two files to the bucket: one for public access and one for private access.
1. Public Object Configuration - Configure the public object so that anyone with its URL can view it, using an appropriate bucket policy or CloudFront.
1. Private Object Configuration - Keep the private object accessible only to authorized IAM users through appropriate IAM permissions.
1. Bucket Policy Configuration - Configure permissions for the public object without granting public access to the entire bucket.
1. IAM Permission Assignment - Assign the required s3:GetObject permission to authorized users for the private object.
1. Public Access Testing - Open the public object's URL in a browser or incognito window and verify that it can be viewed without signing in.
1. Private Access Testing - Open the private object's URL without authentication and verify that access is denied.
1. Authorized Access Testing - Verify that an authorized IAM user can access the private object using the AWS Console or a presigned URL.
10. Security Verification - Confirm that the public object is accessible as intended and the private object remains protected.

Acceptance Criteria

- Create an S3 bucket with a unique name.
- Upload one public object and one private object.
- Configure public access for only the intended public object.
- Keep the private object restricted to authorized IAM users.
- Verify public access using the object's URL in an incognito browser.
- Verify that the private object is inaccessible without authorization.
- Confirm that an authorized user can access the private object.
Important: S3 blocks public access by default. To make an object publicly readable, you may need to adjust the relevant Block Public Access settings and apply a carefully scoped bucket policy. Never disable protections broadly or make the entire bucket public just to expose one file. For private sharing, a presigned URL is another option, but anyone holding that URL can use it until it expires.

## Attachments

- [screenshot-2026-10-13_16-57-17.png](attachments/screenshot-2026-10-13_16-57-17.png)
- [screenshot-2026-10-13_16-58-03.png](attachments/screenshot-2026-10-13_16-58-03.png)
