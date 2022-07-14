# AWS Solutions Architect Associate (SAA-C02) course notes

## Intro

**AWS (Amazon Web Services)** is a Cloud Provider. They provide you with servers and services that you can use *on demand* and *scale easily*.

Services examples:
![image](https://user-images.githubusercontent.com/68676177/178138950-990711fc-763d-4a25-b262-1c40700f6148.png)

## Geography

### Regions
AWS *has regions all around the world*.

> Region is a cluster of data centers.

Names can be us-east-1, eu-west-2 and etc. Most AWS services are region-scoped.
<p align="center">
  <img width="350" height="300" src="https://user-images.githubusercontent.com/68676177/178139508-dd6698ab-2ed5-45cd-8954-441237469d54.png">
</p>

How to choose an AWS Region?
- **Compliance with data governance and legal requirements:** data never leaves a region without your explicit permission.
- **Proximity to customers:** reduced latency.
- **Available services within a Region:** new services and new features aren’t available in every Region.
- **Pricing:** pricing varies region to region and is transparent in the service pricing page.

### Availability Zones (AZ)

Each *region has many availability zones* (usually 3, min is 2, max is 6). Example:
<p align="center">
  <img width="350" height="300" src="https://user-images.githubusercontent.com/68676177/178140056-02275227-afe8-4fa6-9158-f31c1c898683.png">
</p>

- Each availability zone is one or more discrete data centers with redundant power, networking and connectivity.
- They’re separate from each other, so that they’re isolated from disasters.
- They’re connected with high bandwidth, ultra-low latency networking.

### Points of Presence (Edge Locations)
Amazon has *216 Points of Presence (205 Edge Locations & || Regional Caches) in 84 cities across 42 countries*. Content is delivered to end users with *lower latency*.

<p align="center">
  <img width="650" height="300" src="https://user-images.githubusercontent.com/68676177/178140428-05a60948-8549-4353-ba1e-96233b211c2f.png">
</p>

## IAM
**IAM** is **Identity and Access Management** service.
<p align="center">
  <img width="200" height="200" src="https://user-images.githubusercontent.com/68676177/178140709-c31ee508-855b-456f-acdf-5187f7080f8f.png">
</p>

- It is **Global**.
- **Root account** created by default, shouldn’t be used or shared.
- **Users** are people within your organisation, and can be **grouped**.

### Users & Groups

**User** represents one user in your organization. User can be grouped together in **Groups**.
<p align="center">
  <img width="800" height="180" src="https://user-images.githubusercontent.com/68676177/178142768-d70fbb51-2b3d-424d-bc2b-80aea0dc3b50.png">
</p>

- Groups only contain users, not other groups.
- Users don’t have to belong to a group, and user can belong to multiple groups.

### Permissions

**Permissions** is a way to control what user can and cannot do.
<p align="center">
  <img width="300" height="300" src="https://user-images.githubusercontent.com/68676177/178300670-bb603809-adf3-470e-b9ba-0162ad52e342.png">
</p>

- **Users or Groups** can be assigned JSON documents called **policies**.
- These policies define the **permissions** of the users.
- In AWS you apply **the least privilege principle**: don’t give more permissions than a user needs.

Using root account is **dangerous** because it has all the permissions and another admin account should be created and used with **subset of root user permissions**.

### Policies
**Policy** is an object that, when associated with an identity or resource, *defines their permissions*.

<p align="center">
  <img width="350" height="300" src="https://user-images.githubusercontent.com/68676177/178304824-e382a864-4e3d-42a4-9ce9-f79c8ff99e99.png">
</p>

Policy can be assigned to a group and individual user - in this case it’s called **inline**.
<p align="center">
  <img width="700" height="300" src="https://user-images.githubusercontent.com/68676177/178303681-3f88e330-0d72-4643-b8de-b8e6d569a75e.png">
</p>

Policy consists of:
- **Version**: policy language version, *always include "2012-10-17"*
- **Id**: identifier for the policy (*optional*)
- **Statement**: one or more individual statements (*required*)

Statement consists of:
- **Sid**: an identifier for the statement (*optional*)
- **Effect**: whether the statement allows or denies access (*Allow*, *Deny*)
- **Action**: list of actions this policy allows or denies
- **Resource**: list of resources to which the actions applied to
- **Condition**: conditions for when this policy is in effect (*optional*)

### Password policy

Strong passwords make your account more secure. In AWS, you can setup a password policy:
- Set a *minimum password length*
- Require *specific character types*:
  - including *uppercase letters*
  - *lowercase letters*
  - *numbers*
  - *non-alphanumeric* characters
- Allow all IAM users to *change their own passwords*
- *Require users to change their password* after some time (password expiration)
- *Prevent password re-use*

### Multi Factor Authentication - MFA

Main benefit of MFA is that if password is stolen or hacked, the account is not compromised.
- Users have access to your account and can possibly change configurations or delete resources in your AWS account.
- **You want to protect your Root Accounts and IAM users.**
- MFA = password *you know* + security device *you own*.

<p align="center">
  <img width="700" height="100" src="https://user-images.githubusercontent.com/68676177/178996867-95fae309-c68b-4c6d-b380-68e30c752e3e.png">
</p>

MFA devices options in AWS:
- Virtual MFA device (i. e. "Google Authenticator", "Authy"). Providers support for multiple tokens on a single device.
- Universal 2nd Factor (U2F) Security Key (i. e. "Yubikey" by Yubico). Support for multiple root and IAM users using a single sucurity key.
- Hardware Key Fob MFE Device provided by Gemalto.
- Hardware Key Fob MFA device for AWS GovCloud (US) provided by SurePassID.
