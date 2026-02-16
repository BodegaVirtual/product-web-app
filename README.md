# Product Public Web App

A fast, responsive, and SEO-friendly public storefront for the [GraphQL Product Service](https://github.com/BodegaVirtual/graphql-product-service). This application allows customers to browse product catalogs, manage a shopping cart, and complete secure purchases using PayPal.

---

## 🚀 Features

* **Dynamic Catalog**: Browse products by categories with real-time availability updates.
* **Product Search**: Efficient search and filtering powered by the backend GraphQL GSI.
* **Shopping Cart**: Client-side cart persistence for a seamless user experience.
* **PayPal Integration**: Secure checkout flow using PayPal's "Create" and "Capture" order logic.
* **Optimized Performance**: High-speed delivery via AWS CloudFront and S3.
* **Responsive UI**: Fully mobile-optimized design for shopping on any device.

---

## 🛠 Tech Stack

* **Frontend**: React.js
* **Data Fetching**: Apollo Client (GraphQL)
* **Payments**: PayPal JavaScript SDK
* **Styling**: Tailwind CSS
* **Build Tool**: Vite
* **Hosting**: AWS S3 + CloudFront

---

## 📦 Getting Started

### Prerequisites

* **Node.js**: v20.x or higher
* **NPM/Yarn**: Latest stable version
* **Backend API**: The [GraphQL Product Service](https://github.com/BodegaVirtual/graphql-product-service) must be deployed to provide the public API endpoint.

### Installation

1.  **Clone the repository**:
    ```bash
    git clone [https://github.com/BodegaVirtual/product-web-app.git](https://github.com/BodegaVirtual/product-web-app.git)
    cd product-web-app
    ```

2.  **Install dependencies**:
    ```bash
    npm install
    ```

3.  **Configure Environment**:
    Create a `.env` file in the root directory:
    ```env
    VITE_GRAPHQL_PUBLIC_URI=[https://your-api-endpoint.amazonaws.com/v1/public/graphql](https://your-api-endpoint.amazonaws.com/v1/public/graphql)
    VITE_PAYPAL_CLIENT_ID=your_paypal_sandbox_client_id
    ```

4.  **Run Locally**:
    ```bash
    npm run dev
    ```

---

## 🚢 Deployment

This application is designed to be hosted as a static site.

1. **Build the project**:
  ```bash
  npm run build
  ```

2. **Sync to S3**:
The output in the `dist/` folder should be uploaded to the `WebAppS3Bucket` created by the backend SAM template.
  ```bash
  aws s3 sync dist/ s3://your-webapp-s3-bucket-name --delete
  ```

3. **Invalidate Cache**:
To reflect changes immediately on the web:
  ```bash
  aws cloudfront create-invalidation --distribution-id YOUR_DIST_ID --paths "/*"
  ```

---

## 📂 Project Structure

* **`src/components`**: Storefront UI components (Navbar, Product Cards, Cart Modal).
* **`src/hooks`**: Custom hooks for cart logic and PayPal interactions.
* **`src/graphql`**: Public queries for fetching products and categories.
* **`src/pages`**: View components (Home, Category View, Product Detail, Checkout).
* **`public/`**: Images, manifest, and favicon.

---

## 🌐 Demo Environment
Use the following credentials to test the live demo applications:

| Application | URL | User | Password |
| :--- | :--- | :--- | :--- |
| **Customer App** | https://appdemo.bolito.co/ | N/A | N/A |

---

## ⚖️ License & Liability
This project is licensed under the **Apache License 2.0**.

### Limitation of Liability
This software is provided "AS IS", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability or fitness for a particular purpose. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.
