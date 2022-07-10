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
