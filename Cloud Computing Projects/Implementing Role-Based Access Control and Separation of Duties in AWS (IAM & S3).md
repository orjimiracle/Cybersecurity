**Project Title:**  
 **Implementing Role-Based Access Control and Separation of Duties in AWS (IAM & S3)**

**Summary:**  
 This project demonstrates the use of AWS Identity and Access Management (IAM) to enforce **Role-Based Access Control (RBAC)** and **Separation of Duties (SoD)** in a cloud environment. It showcases how access to AWS services and resources like S3 buckets is restricted based on job roles, aligning with best practices in cloud security.

**Objective:**  
 To securely manage permissions and resource access by organizing users into groups with specific policies. This ensures users only access what is relevant to their role, preventing unauthorized access to sensitive data.

**IAM Groups and Their Access Rights:**

1. **Security Team**

   * Full access to CloudTrail logs stored in the `secloginfo` S3 bucket.

   * Role: Review and monitor logs for security auditing.

2. **Developer/Engineer Team**

   * Access only to the `fiistcoderepo` S3 bucket.

   * Role: Upload, retrieve, and manage project files.

   * Cannot view or access security logs or billing data.

3. **Finance Team**

   * Handles AWS billing and cost management only.

   * Role: View and manage billing, with no access to infrastructure (e.g., EC2, S3).

**Users and Their Roles:**

* **David** (Developer)

  * Can access only the `fiistcoderepo` bucket.

  * Denied access to `secloginfo` for security reasons.

* **Sarah** (Security Analyst)

  * Can access `secloginfo` to review AWS CloudTrail logs.

* **John** (Billing Manager)

  * Has permissions to manage billing; cannot access EC2 or S3.

**S3 Buckets:**

1. **secloginfo**

   * Stores CloudTrail logs.

   * Only accessible to the Security Team.

2. **fiistcoderepo**

   * Stores project files.

   * Accessible only by Developers.

**Access Control Policy for Developers:**

json  
CopyEdit  
`{`  
    `"Version": "2012-10-17",`  
    `"Statement": [`  
        `{`  
            `"Sid": "Statement0",`  
            `"Effect": "Allow",`  
            `"Action": "s3:ListAllMyBuckets",`  
            `"Resource": "*"`  
        `},`  
        `{`  
            `"Sid": "Statement1",`  
            `"Effect": "Allow",`  
            `"Action": [`  
                `"s3:ListBucket",`  
                `"s3:PutObject",`  
                `"s3:GetObject",`  
                `"s3:PutBucketPolicy",`  
                `"s3:GetBucketPolicy"`  
            `],`  
            `"Resource": [`  
                `"arn:aws:s3:::fiistcoderepo",`  
                `"arn:aws:s3:::fiistcoderepo/*"`  
            `]`  
        `},`  
        `{`  
            `"Sid": "Statement2",`  
            `"Effect": "Deny",`  
            `"Action": [`  
                `"s3:GetObject",`  
                `"s3:PutObject",`  
                `"s3:DeleteObject"`  
            `],`  
            `"Resource": [`  
                `"arn:aws:s3:::secloginfo",`  
                `"arn:aws:s3:::secloginfo/*"`  
            `]`  
        `}`  
    `]`  
`}`

**Key Concepts Demonstrated:**

* **Role-Based Access Control (RBAC):**  
   Users are granted permissions based on their job roles (Developer, Security Analyst, Billing Manager).

* **Separation of Duties (SoD):**  
   No single user has access to all critical functions. Each user is restricted to only what they need to perform their responsibilities.

* **Principle of Least Privilege:**  
   All users and groups are granted only the minimum permissions required.

**Conclusion:**  
 This project is a practical example of securing cloud environments using AWS IAM and S3. It reinforces the importance of controlled access and accountability, key pillars in modern cloud security. By applying RBAC and SoD, we prevent privilege misuse, enhance security posture, and align with compliance standards.

