## Technical Lab Report: Optimizing Costs of Amazon S3 Object Storage

### 1. Objective

The objective of this task was to implement **Amazon S3 Lifecycle Policies** to manage the growing size and cost of the versioned S3 bucket. The strategy involves automatically transitioning older object versions to a lower-cost storage class and ultimately deleting them after a defined period.

---

### 2. Procedure: Setting Lifecycle Policies

Lifecycle policies were configured on the website bucket to automate the storage management of previous object versions, thereby optimizing storage costs. Two separate, distinct rules were created to meet the requirements.

#### 2.1 Rule 1: Transitioning to S3 Standard-IA

This rule was designed to automatically transition previous object versions to a less expensive storage tier for infrequent access.

* **Action:** Transition noncurrent versions of objects.
* **Target Storage Class:** **S3 Standard-Infrequent Access (S3 Standard-IA)**.
* **Timeframe:** After **30 days** from becoming a noncurrent version.

#### 2.2 Rule 2: Expiring Previous Versions

This rule was designed to permanently delete previous object versions that are no longer needed after a year.

* **Action:** Permanently delete noncurrent versions of objects.
* **Timeframe:** After **365 days** from becoming a noncurrent version.

> **Note:** To ensure precise control over policy application, especially in complex environments, best practice suggests scoping rules using **object tags** rather than applying them globally to all objects.

---

### 3. Result: Verification of Lifecycle Configuration

The S3 bucket's Lifecycle configuration now contains two separate and active rules, ensuring automated cost management:

| Rule Action | Target | Timeframe | Storage Class/Action |
| :--- | :--- | :--- | :--- |
| **Transition** | Previous Versions | After 30 days | S3 Standard-IA |
| **Expiration** | Previous Versions | After 365 days | Permanent Delete |

The implemented configuration successfully addresses cost concerns by transitioning infrequently accessed older versions and eventually retiring them.

![Lifecycle Policy](./public/assets/life_cycle.png)