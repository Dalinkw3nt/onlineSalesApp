# RetailEdge Lite - Cloud-Based POS & Sales Dashboard

RetailEdge Lite is a scalable, cloud-based **Point of Sale (POS) and Sales Dashboard** solution for small retailers. Built on **AWS** with **React Native** for mobile and **React** for the dashboard, it integrates **Yoco Payment Gateway** for secure transactions.

## **Features**
- **Cloud-Based POS System** (React Native, AWS Lambda, DynamoDB)
- **Smart Inventory Tracking** (DynamoDB, Amazon SNS for low-stock alerts)
- **Real-Time Sales Dashboard** (React + AWS QuickSight)
- **Yoco Payment Gateway Integration** (Card payments via Yoco SDK)
- **Offline Mode** (Transactions sync to AWS after internet recovery)
- **Scalable & Cost-Effective AWS Infrastructure** (Serverless architecture)
- **CI/CD Pipeline** using GitHub Actions
- **Email Notifications** for deployment status via Gmail SMTP

---
    
## **1. Prerequisites**
- **Node.js** (v16+)
- **AWS CLI** (configured with necessary IAM permissions)
- **Terraform** (for infrastructure provisioning)
- **Yoco API Key** (Register at [Yoco](https://www.yoco.com/))
- **Gmail App Password** for sending email notifications

---

## **2. Deployment Instructions**

### **Step 1: Clone the Repository**
```sh
git clone https://github.com/your-repo/retailedge-lite.git
cd retailedge-lite
```

### **Step 2: Set Up GitHub Secrets**
In your repository settings, add the following secrets:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_S3_BUCKET` (for dashboard deployment)
- `CLOUDFRONT_DISTRIBUTION_ID`
- `GMAIL_USERNAME` (your Gmail address)
- `GMAIL_APP_PASSWORD` (from Google App Passwords)
- `EMAIL_RECEIVER` (recipient of deployment notifications)

### **Step 3: Deploy AWS Infrastructure (Terraform)**
```sh
cd terraform
terraform init
terraform apply -auto-approve
```

### **Step 4: Run CI/CD Pipelines**
GitHub Actions automatically runs on every push to the `main` branch:
- Backend deploys to **AWS Lambda**
- POS system builds and runs tests
- Dashboard builds and deploys to **AWS S3** with **CloudFront**
- Email notifications sent for success or failure

### **Step 5: Run the POS System (React Native)**
```sh
cd pos
npm install
npm start
```

### **Step 6: Run the Sales Dashboard (React Web App)**
```sh
cd salesDashboard
npm install
npm start
```

---

## **3. Yoco Payment Gateway Integration**
- **Set your Yoco Public Key in POS System:**
  ```sh
  export YOCO_PUBLIC_KEY='your-public-key'
  ```
- **Set Yoco Secret Key for Lambda:**
  ```sh
  export YOCO_SECRET_KEY='your-secret-key'
  ```

---

## **4. CI/CD Pipeline Details**
The deployment workflow includes:
- ✅ Automatic deployment upon `main` branch push
- ✅ Email notifications for success and failure via Gmail SMTP
- ✅ Detailed logs for failed deployments

---

## **5. APIs**
### **POS Transactions**
- **Endpoint:** `POST /sales`
- **Payload:**
  ```json
  {
    "saleId": "12345",
    "itemId": "ABC001",
    "quantity": 2
  }
  ```

### **Yoco Payment Processing**
- **Endpoint:** `POST /payments`
- **Payload:**
  ```json
  {
    "saleId": "12345",
    "token": "yoco-payment-token",
    "amount": 100.00
  }
  ```

---

## **6. Security & Authentication**
- **Cognito Authentication** for secure user login.
- **AWS KMS Encryption** for sensitive data.
- **AWS Shield** for DDoS protection.

---

## **7. Next Steps & Enhancements**
✅ Multi-Store Support
✅ Mobile Money Integration (MTN, Vodacom Pay)
✅ Supplier Order Automation

---

## **8. Contributors**
- **CN Musonda** - [GitHub](https://github.com/Dalinkw3nt)


---

## **9. License**
MIT License. See `LICENSE` for details.
