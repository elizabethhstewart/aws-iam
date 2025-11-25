# AWS IAM Fundamentals: Enforcing the Principle of Least Privilege

This project documents a foundational, hands-on exercise designed to practice core security principles and administrative configurations within **AWS Identity and Access Management (IAM)**. The primary focus was on designing and testing granular permissions to ensure strict application of the **Principle of Lease Privilege**.

**Key Concepts Applied**
* **AWS IAM**: Users, Groups, and Group-Based Management
* **Principle of Least Privilege**: Enforced policy design to grant only necessary permissions.
* **Policy Granularity**: Differentiating between Read, Write, and Full Administrative access.
* **Access Verification**: End-to-end testing of restricted user access.

**Lab Objectives and Execution Steps**

The following steps were executed to demonstrate proficiency in IAM setup, custom policy definition, and access control:

1. **Identity Structure Creation**: Created **three distinct IAM Users** and **three dedicated IAM Groups** (Viewers, Operators, Admins) to manage permissions centrally.
2. **Policy Definition & Assignment**: Defined and assigned policies to each group to strictly control access to key services (EC2 and S3):
     * **Group 1** (Viewers): Assigned policies allowing viewing access of EC2 instances, but **explicitly denied** access to stop/start actions and S3 access.
     * **Group 2** (Operators): Assigned policies granting viewing accss to EC2 instances but **denied** access to S3 or any EC2 modification actions.
     * **Group 3** (Admins): Assigned policies granting **full administrative access** to manage and control EC2 instances (including stopping) and full S3 access.
3. **Access Verification (Testing Principle of Least Privilege)**:
     * **User 1 Test**: Successfully verified that the user **did not have access** to view or interact with EC2 instances.
     * **User 2 Test**: Confirmed the user **only had viewing access** to EC2 instances, but attempts to stop the instances failed, and all S3 acesss was denied.
     * **User 3 Test**: Confirmed the user had full control over EC2 instances, including the ability to stop them demonstrating the highest privilege level.
  
  This exercise verfies the practical capability to design, implement, and test a secure, segmented access model within AWS. 

