## ☕ Technical Project Report: Creating a Static Website for the Café

### 1. Project Overview and Objectives

This project utilized **Amazon Simple Storage Service (Amazon S3)** to deploy a static website for a simulated café. The primary objectives were to implement the static website hosting capability of S3 and apply key architectural best practices for data protection, management, and disaster recovery.

---

### 2. Architectural Best Practices and Implementation

#### 2.1 Amazon S3 Hosted Static Website

* **Implementation:** An S3 bucket was configured to serve a static website, hosting HTML, CSS, JavaScript, and image assets for the café.
* **Access Method:** Public access was granted via the S3 Bucket Policy to allow anonymous read access to the `s3:GetObject` action, enabling public web hosting.
    * *Note: For production, this access is often restricted further, such as via an Amazon CloudFront distribution.*
* **Verification:** The website successfully loaded from the S3 endpoint.

![Image](public/assets/website_loaded.png)

#### 2.2 Data Protection: One-Way Implementation

To ensure data integrity and prevent accidental or malicious deletion/overwriting of critical objects, **S3 Object Lock** was implemented.

* **Configuration:** The S3 bucket was configured with Object Lock in **Compliance Mode** for a defined retention period.
* **Result:** This measure makes the objects immutable, meaning they cannot be overwritten or deleted by any user, including the root account, until the retention period expires.

#### 2.3 Data Management: Amazon S3 Lifecycle Strategy

An S3 Lifecycle Rule was implemented to optimize storage costs by automatically transitioning non-critical data to lower-cost storage classes.

* **Strategy:** Objects were configured to transition after a specified number of days to the **S3 Standard-Infrequent Access (S3 Standard-IA)** storage class.
* **Goal:** This strategy ensures that objects not accessed frequently after the initial launch period are moved to a cost-effective tier while remaining readily available.

#### 2.4 Disaster Recovery (DR): Amazon S3 Cross-Region Replication

To implement a robust Disaster Recovery strategy, **Cross-Region Replication (CRR)** was configured.

* **Source/Destination:** A replication rule was set up to automatically and asynchronously copy all objects from the **Source S3 Bucket** (in Region A) to a **Destination S3 Bucket** (in Region B).
* **Value:** This provides geographic redundancy, ensuring that the website data remains available and recoverable in the event of a regional outage or major data loss incident in the source region.

---

### 3. Deliverables Summary

| Deliverable | Status | Implementation Details |
| :--- | :--- | :--- |
| Amazon S3 hosted static website | **Completed** | S3 bucket configured for website hosting with index and error documents. |
| One-way implementation to protect data | **Completed** | **S3 Object Lock** configured in **Compliance Mode**. |
| Amazon S3 lifecycle strategy implemented | **Completed** | Rule implemented to transition objects to **S3 Standard-IA**. |
| Amazon S3 disaster recovery (DR) implemented | **Completed** | **Cross-Region Replication (CRR)** established between two distinct AWS Regions. |