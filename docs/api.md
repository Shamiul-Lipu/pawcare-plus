# API Documentation for PawCare+

This document outlines the various API endpoints used by PawCare+, categorized by feature area.

## **1. Marketplace (Food + Accessories)**

### 1.1 Product Browsing

- **GET** `/products?category=&filters=&search=&sort=&page=`
  - **Parameters**:
    - `category`: The category of products (e.g., food, toys, accessories).
    - `filters`: Filters such as pet type, breed, age, diet.
    - `search`: Search term for products.
    - `sort`: Sorting option (e.g., price, rating).
    - `page`: Page number for pagination.

### 1.2 Product Details

- **GET** `/products/:id`
  - **Parameters**:
    - `id`: Product ID.
- **GET** `/reviews?productId=`
  - **Parameters**:
    - `productId`: Product ID to fetch reviews for.

### 1.3 Cart & Orders

- **POST** `/cart`
  - **Body**: Add products to the cart.
- **GET** `/cart`

  - **Response**: Returns the current user's cart.

- **POST** `/orders`

  - **Body**: Create a new order.

- **GET** `/orders/:id`

  - **Parameters**:
    - `id`: Order ID.

- **PATCH** `/orders/:id/status`
  - **Parameters**:
    - `id`: Order ID.
    - `status`: New order status.

### 1.4 Wishlist

- **POST** `/wishlist`

  - **Body**: Add item to the wishlist.

- **GET** `/wishlist`

  - **Response**: Returns the user's wishlist.

- **DELETE** `/wishlist/:productId`
  - **Parameters**:
    - `productId`: Product ID to remove from the wishlist.

## **2. Vet Appointment System**

### 2.1 Vet Discovery

- **GET** `/vets?search=&location=&specialty=&sort=`
  - **Parameters**:
    - `search`: Vet search query.
    - `location`: Filter by location.
    - `specialty`: Filter by specialty.
    - `sort`: Sorting option (e.g., rating, availability).

### 2.2 Appointment Booking

- **GET** `/vets/:id/availability`

  - **Parameters**:
    - `id`: Vet ID to check availability.

- **POST** `/appointments`
  - **Body**: Book an appointment.

### 2.3 Appointment Management

- **PATCH** `/appointments/:id`

  - **Parameters**:
    - `id`: Appointment ID.
    - `status`: New appointment status (e.g., cancelled, rescheduled).

- **GET** `/appointments?userId=`
  - **Parameters**:
    - `userId`: User ID to fetch appointments.

## **3. AI Symptom Checker**

### 3.1 Input Collection

- **POST** `/ai/symptom-check`
  - **Body**: Symptoms input by the user.

### 3.2 AI Diagnosis

- **GET** `/ai/diagnosis`
  - **Response**: Diagnosis details.

## **4. AI Nutrition Assistant**

### 4.1 Diet Input

- **POST** `/ai/nutrition-plan`
  - **Body**: Diet input data (age, weight, breed, etc.).

### 4.2 AI Recommendations

- **GET** `/products?recommendedFor=dietPlan`
  - **Parameters**:
    - `dietPlan`: The specific diet plan ID for recommended products.

---

---

### `architecture.md`

````markdown
# Architecture Overview for PawCare+

The architecture of PawCare+ is designed to be scalable, efficient, and modular, ensuring a smooth user experience and quick performance.

## **High-Level Architecture Diagram**

![Architecture Diagram](path/to/diagram.png)

## **Components:**

### 1. **Frontend**

- **React.js**: Handles the user interface for the web and mobile application.
- **Redux**: Manages the global state of the application, including cart, wishlist, and user authentication.
- **Map API Integration**: Used for features like shelter directory, lost & found, and vet location discovery.

### 2. **Backend**

- **Node.js with Express**: Serves the API endpoints for managing products, users, appointments, and more.
- **Database**:
  - **MongoDB**: Stores user data, products, appointments, reviews, etc.
  - **Redis**: Caches frequently accessed data to reduce response time (e.g., popular products).
- **AI Models**:
  - Symptom checker and nutrition assistant powered by machine learning models.

### 3. **Database Models**

- **User**: Stores user credentials, profile data, pet profiles.
- **Product**: Contains product details like name, price, stock, and attributes (breed, diet, etc.).
- **Order**: Stores order details, including items, total, status, and payment info.
- **Appointment**: Stores vet appointment details.
- **Review**: Manages user reviews for products and vets.

### 4. **External Services**

- **Payment Gateway**: Used for processing payments.
- **SMS/Email Service**: For appointment reminders, notifications, and user alerts.
- **AI Services**: Used for the symptom checker and diet recommendations.

---

### **Scalability Considerations**

To ensure the system can handle future growth, PawCare+ uses:

- **Load Balancers**: Distribute traffic evenly across backend servers.
- **Microservices**: Components like product management, cart, and vet appointments are split into services that can scale independently.
- **Database Sharding**: Large datasets, such as product inventories, are stored across multiple database instances for high availability.

---

### **Security Measures**

- **JWT Authentication**: For secure and stateless user authentication.
- **Encryption**: Sensitive data such as user credentials and payment information is encrypted.
- **Role-Based Access Control (RBAC)**: Ensures that only authorized users have access to certain resources (e.g., admin panel).

---

### `workflows.md`

```markdown
# Workflows for PawCare+

This document outlines the key workflows for the PawCare+ platform. These workflows represent user journeys or system processes within the platform.

## **1. User Journey: Product Browsing**

1. **Product Search**:
   - The user inputs search criteria in the search bar.
   - The API filters products based on category, pet type, breed, age, diet, brand, price, and rating.
   - The system displays the products in a paginated list.
2. **Filter and Sort**:

   - The user applies filters (e.g., breed, age).
   - The API applies additional filters on top of the search query.
   - Products are sorted by rating, price, or relevance.

3. **View Product**:

   - Clicking on a product displays its detailed page, including description, reviews, seller info, and related products.

4. **Add to Cart**:
   - User selects quantity and adds the product to their cart.

---

## **2. Vet Appointment Workflow**

1. **Discover Vets**:
   - User searches for vets by location and specialty.
   - The system filters the list of available vets based on search parameters.
2. **Book Appointment**:

   - User selects a vet, chooses appointment type (in-clinic or telemedicine), and selects a date/time slot.
   - The system locks the slot and confirms the booking.

3. **Appointment Management**:
   - The user can cancel or reschedule appointments through the app.
   - Notifications are sent for upcoming appointments or changes.

---

## **3. AI Symptom Checker Workflow**

1. **Input Symptoms**:

   - The user inputs symptoms and selects pet details (age, type, etc.).
   - The AI receives the input and processes it.

2. **Diagnosis**:

   - AI generates a potential diagnosis with severity levels and home-care steps.
   - The system recommends a vet visit based on the urgency of the condition.

3. **Save Logs**:
   - The AI diagnosis is saved in the user’s log for future reference.

---

## **4. Order and Checkout Workflow**

1. **Add Products to Cart**:

   - The user adds products to the cart, selecting quantity and any necessary details (e.g., size, color).

2. **Checkout Process**:

   - User enters delivery address and payment details.
   - The system validates stock and calculates the total price.
   - Order is placed, and a confirmation is sent to the user.

3. **Track Order**:
   - The user can track the order’s status in real-time, receiving updates on shipping, delivery, or any issues.

---

### **5. Lost & Found Workflow**

1. **Create Report**:

   - User uploads a pet photo and provides details such as last-seen location and description.
   - The system creates a lost or found report and notifies nearby users.

2. **View Reports**:

   - Users can filter and view lost/found reports based on proximity and type.

3. **User Alerts**:
   - Users receive alerts when a nearby report is created, allowing them to contact the owner directly.
```
````
