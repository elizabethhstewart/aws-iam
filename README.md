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
2. **[User Assignment](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/IAM%20users%20and%20user%20groups.png)**: Assigned each user to their specific group to align with defined job roles (e.g., `user-1` to `S3-Support`)
3. **Policy Definition & Assignment**: Attached policies to each group to striclty control access to AWS resources:
     * `S3-Support` **Group**: Granted Read-Only access to Amazon S3. 
     * `EC2-Support` **Group**: Granted Read-Only access to Amazon EC2.
     * `EC2-Admin` **Group**: Granted EC2 Administrative control with permissions to view, start, and stop Amazon EC2 instances, while access to other services (e.g., S3) was restricted or not granted.
  
_Each user was assigned to a user group with special permissions. The layout is visualized below:_

|  User  |  User Group |                  Permissions               |
|--------|-------------|--------------------------------------------|
| User-1 |  S3-Support |        Read-Only access to Amazon S3       |
| User-2 | EC2-Support |        Read-Only access to Amazon EC2      |
| User-3 |  EC2-Admin  | View, Start, and Stop Amazon EC2 instances |

4. **Access Verification** (Testing Principle of Least Privilege): Successfully logged in as each user to validate policy effectiveness against the requirements:

    * **User 1 Test (`S3-Support`):** Successfully [accessed S3](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-1%20S3%20Access.png) in a [Read-Only capacity](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-1%20S3%20View%20Only%20Access.png), while all [EC2 access](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-1%20Restricted%20EC2%20Access.png) was strictly denied.
        
    * **User 2 Test (`EC2-Support`):** Confirmed the unauthorized access to [S3 services](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-2%20Restricted%20S3%20Access.png) and successfully [accessed and viewed](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-2%20Viewing%20Instances.png) EC2 instances, but attempts to [Start or Stop instances](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-2%20Restricted%20Stopping%20Instance.png) were explicitly denied, enforcing the Read-Only restriction. 
    * **User 3 Test (`EC2-Admin`):** Confirmed full operational control over [EC2 instances](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-3%20Stopped%20Instance.png) (View, Start, Stop), while verifying the absence of [unauthorized access to services like S3](https://github.com/elizabethhstewart/aws-iam/blob/4e693e61b19dc57af8018be88e294b1369bb2078/assets/User-3%20Restricted%20S3.png).
   
  This exercise verfies the practical capability to design, implement, and test a secure, segmented access model within AWS. 

