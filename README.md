# AWS IAM Fundamentals: Enforcing the Principle of Least Privilege

This project documents a foundational, hands-on exercise designed to practice core security principles and administrative configurations within **AWS Identity and Access Management (IAM)**. The primary focus was on designing and testing granular permissions to ensure strict application of the **Principle of Least Privilege**.

**Key Concepts Applied**
* **AWS IAM**: Users, Groups, and Group-Based Policy Management
* **Role-Based Access Control**: Implementing permissions based on job function (Support vs. Admin)
* **Principle of Least Privilege**: Enforced policy design to grant only necessary permissions.
* **Policy Granularity**: Differentiating between Read-Only, View, and Operational control.
* **Access Verification**: End-to-end testing of restricted user access.

**Lab Objectives and Execution Steps**

The following steps were executed to demonstrate proficiency in IAM setup, custom policy definition, and access control:

1. **Identity Structure Creation**: Created **three distinct IAM Users**(`user-1`, `user-2`, `user-3`) and **three dedicated IAM Groups** (`S3-Support`, `EC2-Support`, `EC2-Admin`) to manage permissions centrally.
2. **User Assignment**: Assigned each user to their specific group to align with defined job roles (e.g., `user-1` to `S3-Support`)
3. **Policy Definition & Assignment**: Attached policies to each group to striclty control access to AWS resources:
     * `S3-Support` **Group**: Granted Read-Only access to Amazon S3. 
     * `EC2-Support` **Group**: Granted Read-Only access to Amazon EC2.
     * `EC2-Admin` **Group**: Granted EC2 Administrative control with permissions to view, start, and stop Amazon EC2 instances, while access to other services (e.g., S3) was restricted or not granted.

4. **Access Verification** (Testing Principle of Least Privilege): Successfully logged in as each user to validate policy effectiveness against the requirements:

    * **User 1 Test (`S3-Support`):** Successfully accessed S3 in a Read-Only capacity, while all EC2 access was strictly denied.
        * **Proof:** [Verification Screenshot: User 1 EC2 Access Denied](assets/User-1 Restricted EC2 Access.png/README.md)
    * **User 2 Test (`EC2-Support`):** Successfully accessed and viewed EC2 instances, but attempts to Start or Stop instances were explicitly denied, enforcing the Read-Only restriction.
    * **User 3 Test (`EC2-Admin`):** Confirmed full operational control over EC2 instances (View, Start, Stop), while verifying the absence of unauthorized access to services like S3.
   
  This exercise verfies the practical capability to design, implement, and test a secure, segmented access model within AWS. 

