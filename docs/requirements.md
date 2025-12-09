# 🐾 **PawCare+ : Feature Requirements**

**Purpose → convert directly into tasks, API endpoints, DB models, UI components.**

---

### **1. Marketplace (Food + Accessories)**

---

## **1.1 Product Browsing**

### **Sub-features**

- Category-based browsing
- Filters: pet type, breed, age, diet
- Filters: brand, price, rating
- Search bar
- Pagination or infinite scroll

### **Developer Requirements**

**API**

> GET /products?category=&filters=&search=&sort=&page=

**Database**

- Product model with:

  - category
  - attributes (breed, age, diet, brand)
  - price
  - stock
  - rating
  - sellerId

**Backend Logic**

- Filtering, sorting, text search
- Seller join + rating aggregation

---

## **1.2 Product Details**

### **Sub-features**

- Detailed product description
- Ingredients (for food)
- Reviews & ratings
- Seller details
- Related products

### **Developer Requirements**

**API**

> GET /products/:id
> GET /reviews?productId=

**Database**

- Review model (userId, productId, rating, comment, createdAt)

**Backend Logic**

- Compute average rating
- Fetch seller info
- Recommend related items

---

## **1.3 Cart & Orders**

### **Sub-features**

- Add/update/remove items
- Checkout flow
- Order creation
- Order tracking
- Subscription ordering
- Coupons support

### **Developer Requirements**

**API**

> POST /cart
> GET /cart
> POST /orders
> GET /orders/:id
> PATCH /orders/:id/status
> POST /subscriptions

**Database**

- Cart model
- Order model (items, total, status, address, paymentStatus)
- Subscription model

**Backend Logic**

- Cart total calculation
- Stock/inventory validation
- Order lifecycle handling

---

## **1.4 Wishlist**

### **Sub-features**

- Add/remove wishlist item
- View wishlist

### **Developer Requirements**

**API**

> POST /wishlist
> GET /wishlist
> DELETE /wishlist/:productId

**Database**

- Wishlist model (userId, productIds[])

**Backend Logic**

- Toggle wishlist
- Prevent duplicates

---

# ## **2. Vet Appointment System**

---

## **2.1 Vet Discovery**

### **Sub-features**

- Search by location
- Filter by specialty
- Sort by rating/availability

### **Developer Requirements**

**API**

> GET /vets?search=&location=&specialty=&sort=

**Database**

- Vet model (specialization, location, rating, availability)

**Backend Logic**

- Geo-based search
- Rating aggregation

---

## **2.2 Appointment Booking**

### **Sub-features**

- Choose in-clinic or telemedicine
- Select date/time
- Confirm booking

### **Developer Requirements**

**API**

> GET /vets/:id/availability
> POST /appointments

**Database**

- Appointment model (vetId, userId, type, date, time, status)

**Backend Logic**

- Slot locking
- Telemedicine session generation

---

## **2.3 Appointment Management**

### **Sub-features**

- Cancel/reschedule
- View appointment history
- Reminder notifications

### **Developer Requirements**

**API**

> PATCH /appointments/:id
> GET /appointments?userId=

**Backend Logic**

- Reminder cron jobs
- In-app + email notifications

---

### **3. AI Symptom Checker**

---

## **3.1 Input Collection**

### **Sub-features**

- Pet type, age
- Multi-symptom selection
- Optional notes

### **Developer Requirements**

**API**

> POST /ai/symptom-check

**Backend Logic**

- Parse user input
- Prepare AI prompt

---

## **3.2 AI Diagnosis**

### **Sub-features**

- Predicted causes
- Severity level
- Home-care steps
- Recommend vet visit

### **Developer Requirements**

**AI Response Format**

```json
{
  "causes": [],
  "homeCare": [],
  "urgencyLevel": "low | medium | high",
  "recommendVetVisit": true
}
```

**Backend Logic**

- AI model call
- Validate AI output

---

## **3.3 Logs**

### **Developer Requirements**

**API**

> GET /ai/symptom-logs

**Database**

- SymptomsLog (userId, petId, inputData, result)

---

### **4. AI Nutrition Assistant**

---

## **4.1 Diet Input**

### **Sub-features**

- Age, weight, breed
- Allergies
- Diet patterns
- Health goals

### **Developer Requirements**

**API**

> POST /ai/nutrition-plan

---

## **4.2 AI Recommendations**

### **Sub-features**

- Feeding schedule
- Diet plan
- Nutrition table
- Recommended products

### **Developer Requirements**

**Backend Logic**

- AI prompt for diet generation

**API**

> GET /products?recommendedFor=dietPlan

---

### **5. Pet Profiles & Medical Records**

---

## **5.1 Pet Profiles**

### **Sub-features**

- Create/edit pet profile
- Upload pet photo
- Breed/age/weight tracking

### **Developer Requirements**

**API**

> POST /pets
> GET /pets
> PATCH /pets/:id

**Database**

- Pet model

---

## **5.2 Medical Records**

### **Sub-features**

- Add vaccination entries
- Add medication entries
- Allergy log
- Upload medical documents

### **Developer Requirements**

**API**

> POST /pets/:id/records
> GET /pets/:id/records

**Database**

- MedicalRecord model

---

## **5.3 Reminders**

### **Developer Requirements**

**API**

> GET /reminders

**Database**

- Reminder model

**Backend Logic**

- Cron jobs
- Notification sender

---

### **6. Lost & Found System**

---

## **6.1 Create Report**

### **Sub-features**

- Upload pet photo
- Description
- Last-seen location
- Lost/Found status

### **Developer Requirements**

**API**

> POST /lost-found

**Database**

- LostFoundReport

---

## **6.2 View Reports**

### **Sub-features**

- Map view
- List view
- Filter by type
- Filter by distance

### **Developer Requirements**

**API**

> GET /lost-found?type=&location=

**Backend Logic**

- Geo search

---

## **6.3 User Alerts**

### **Sub-features**

- Notify nearby users
- Contact report owner

### **Developer Requirements**

**API**

> POST /lost-found/:id/contact

**Backend Logic**

- Geo-proximity notifications

---

### **7. Shelters Map**

---

## **7.1 Shelter Directory**

### **Sub-features**

- List shelters
- Search by location

### **Developer Requirements**

**API**

> GET /shelters?location=

**Database**

- Shelter model

---

## **7.2 Map Integration**

### **Sub-features**

- Display shelter pins
- Detailed card on-click
- Directions link

### **Developer Requirements**

**Frontend**

- Map API integration

---

### **8. Dashboards (Role-Based)**

---

## **8.1 User Dashboard**

- View orders
- View appointments
- Reminders
- Saved items

## **8.2 Vet Dashboard**

- Appointment calendar
- Patient history
- Add notes
- Telemedicine sessions

## **8.3 Seller Dashboard**

- Manage products
- View orders
- Inventory management
- Sales analytics

## **8.4 Admin Dashboard**

- Manage users/vets/sellers
- Verify vets
- Manage shelters
- Manage lost&found posts
- Platform analytics

---
