# 🛍️ Product Price Comparison Application

Welcome to the **Final Project** of the course! This project demonstrates how to build and deploy a microservices-based product price comparison app using **IBM Cloud Code Engine**. It consists of two backend APIs and one frontend microservice, all integrated seamlessly.

---

## 🎯 Objectives

* ✅ Deploy Python & Node.js backend microservices on IBM Cloud Code Engine
* ✅ Integrate backend APIs with a frontend microservice
* ✅ Validate the complete end-to-end product and pricing workflow
* ✅ Submit required screenshots as proof of completion

---

## 🗂️ Repository Structure

```bash
/home/project
├── dealer_evaluation_backend
│   ├── products_list/       # 📦 Python microservice (Product Details)
│   └── dealer_details/      # 📦 Node.js microservice (Dealer Pricing)
└── dealer_evaluation_frontend/  # 🌐 Frontend microservice
```

---

## 🧱 Part A: Deploy Backend Microservices

### 🔹 Task 1: Deploy Product Details Microservice (Python)

* **Repository:** [https://github.com/ibm-developer-skills-network/dealer\_evaluation\_backend.git](https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git)
* **Context Directory:** `products_list`
* **Port:** `5000`

```bash
ibmcloud ce application create --name prodlist \
  --image us.icr.io/${SN_ICR_NAMESPACE}/prodlist \
  --registry-secret icr-secret \
  --port 5000 \
  --build-context-dir products_list \
  --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
```

📸 Screenshot: `product_details_deploy.png`

---

### 🔹 Task 2: Deploy Dealer Pricing Microservice (Node.js)

* **Context Directory:** `dealer_details`
* **Port:** `8080`

```bash
ibmcloud ce application create --name dealerdetails \
  --image us.icr.io/${SN_ICR_NAMESPACE}/dealerdetails \
  --registry-secret icr-secret \
  --port 8080 \
  --build-context-dir dealer_details \
  --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
```

📸 Screenshot: `dealer_details_deploy.png`

---

## 🖥️ Part B: Deploy Frontend Microservice

### 🔹 Task 3: Clone the Frontend Repository

```bash
cd /home/project
git clone https://github.com/ibm-developer-skills-network/dealer_evaluation_frontend.git
cd dealer_evaluation_frontend
```

📸 Screenshot: `git_clone.png`

---

### 🔹 Task 4: Update Backend URLs in index.html

Update the placeholders in `index.html`:

```javascript
const productsURL = "https://prodlist.***.codeengine.appdomain.cloud/";
const dealerDetailsURL = "https://dealerdetails.***.codeengine.appdomain.cloud/";
```

📸 Screenshot: `index_urlchanges.png`

---

### 🔹 Task 5: Deploy the Frontend Microservice

* **Port:** `5001`

```bash
ibmcloud ce application create --name frontend \
  --image us.icr.io/${SN_ICR_NAMESPACE}/frontend \
  --registry-secret icr-secret \
  --port 5001 \
  --build-source .
```

📸 Screenshot: `frontend_deploy.png`

---

## 🔎 Part C: Verify Functionality

### 🔹 Task 6: View Homepage

* Open frontend URL
* Confirm product dropdown is populated
  📸 Screenshot: `homepage.png`

### 🔹 Task 7: Select Product → View Dealers

📸 Screenshot: `product_dealer.png`

### 🔹 Task 8: Select Dealer → View Price

📸 Screenshot: `product_dealer_price.png`

### 🔹 Task 9: Select All Dealers → View All Prices

📸 Screenshot: `product_all_dealers_prices.png`

---

## 🧾 Screenshot Summary Table

| Screenshot File                  | Description                        |
| -------------------------------- | ---------------------------------- |
| `product_details_deploy.png`     | Python backend deployed            |
| `dealer_details_deploy.png`      | Node.js backend deployed           |
| `git_clone.png`                  | Frontend repo cloned               |
| `index_urlchanges.png`           | URLs updated in index.html         |
| `frontend_deploy.png`            | Frontend deployed on Code Engine   |
| `homepage.png`                   | Homepage with product dropdown     |
| `product_dealer.png`             | Dealers shown for selected product |
| `product_dealer_price.png`       | Price shown for a selected dealer  |
| `product_all_dealers_prices.png` | Prices shown for all dealers       |

---

## ✅ Final Summary

This project demonstrates the practical implementation of a microservices-based architecture using IBM Cloud Code Engine. It integrates a Python-based product details API, a Node.js-based dealer pricing API, and a frontend interface to allow users to compare product prices across multiple dealers. Through this hands-on experience, I’ve learned how to containerize and deploy services, manage API integration, and validate serverless deployments in a scalable cloud-native environment.

---

> 🚀 **Project Completed Successfully!**

NAME - SOUVIK MANDAL
