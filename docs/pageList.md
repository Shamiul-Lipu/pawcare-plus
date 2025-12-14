# 🐾 PawCare+ Web App – Design System & User Flows

---

## 1️⃣ Core User Flows

### 🛒 Marketplace Flow

- **Landing / Products Page** – User lands, sees products, uses search & filters.
- **Product Details Page** – Views detailed info about a product.
- **Add to Cart** – Adds item(s) to cart.
- **Checkout Page** – Reviews cart, enters shipping info, selects payment.
- **Place Order** – Confirms order.
- **Orders Page** – Views all past orders.
- **Order Details Page** – Views specific order details.

### 🐶 Pet Management Flow

- **Create Pet Profile** – Add name, breed, age, photo.
- **Add Medical Records** – Vaccinations, medications, allergies.
- **Set Reminders** – Receive notifications for meds, appointments.

### 🏥 Vet Appointment Flow

- **Search Vets** – Filter by location, specialty, rating.
- **Vet Profile** – View vet info, availability, ratings.
- **Book Appointment** – Choose date/time, type (clinic/telemedicine).
- **Appointment History** – View past and upcoming appointments.

### 🚨 Lost & Found Flow

- **Create Report** – Upload pet photo, description, location, lost/found status.
- **View Reports** – Filter by type or distance, map/list view.
- **Contact Owner** – Send message to report creator.

### 🗺️ Shelter Flow

- **Browse Shelters** – Search by location.
- **View Map** – Click pins for shelter details.

### 📊 Dashboard Flow (Role-Based)

**User Dashboard** – View orders, appointments, reminders, saved items.  
**Vet Dashboard** – Appointment calendar, patient history, telemedicine sessions.  
**Seller Dashboard** – Manage products, inventory, orders, analytics.  
**Admin Dashboard** – Manage users/vets/sellers, shelters, lost & found, analytics.

---

## 🐾 PawCare+ – Final Page List

### 🌐 1. Public & Auth

- `/` – LandingPage
- `/login` – LoginPage
- `/register` – RegisterPage
- `/forgot-password` – ForgotPasswordPage

### 🛒 2. Marketplace

- `/products` – ProductListPage
- `/products/:id` – ProductDetailsPage
- `/cart` – CartPage
- `/checkout` – CheckoutPage
- `/orders` – OrdersPage
- `/orders/:id` – OrderDetailsPage
- `/wishlist` – WishlistPage

### 🏥 3. Vet Appointments

- `/vets` – VetSearchPage
- `/vets/:id` – VetProfilePage
- `/vets/:id/book` – BookAppointmentPage
- `/appointments` – AppointmentsPage
- `/appointments/:id` – AppointmentDetailsPage

### 🤖 4. AI Features

- `/ai/symptom-checker` – SymptomCheckerPage
- `/ai/symptom-history` – SymptomHistoryPage
- `/ai/nutrition` – NutritionAssistantPage

### 🐶 5. Pet Management

- `/pets` – PetListPage
- `/pets/new` – PetCreatePage
- `/pets/:id/edit` – PetEditPage
- `/pets/:id/records` – MedicalRecordsPage
- `/reminders` – RemindersPage

### 🚨 6. Lost & Found

- `/lost-found` – LostFoundListPage
- `/lost-found/new` – LostFoundCreatePage
- `/lost-found/:id` – LostFoundDetailsPage

### 🗺️ 7. Shelters

- `/shelters` – ShelterListPage
- `/shelters/map` – ShelterMapPage

### 📊 8. Dashboards (Protected)

**User**

- `/dashboard` – UserDashboard

**Vet**

- `/vet/dashboard` – VetDashboard
- `/vet/appointments` – VetAppointmentsPage
- `/vet/patients` – PatientHistoryPage
- `/vet/telemedicine/:id` – TelemedicinePage

**Seller**

- `/seller/dashboard` – SellerDashboard
- `/seller/products` – ManageProductsPage
- `/seller/inventory` – InventoryPage
- `/seller/orders` – SellerOrdersPage
- `/seller/analytics` – SalesAnalyticsPage

**Admin**

- `/admin/dashboard` – AdminDashboard
- `/admin/users` – UserManagementPage
- `/admin/vets` – VetVerificationPage
- `/admin/shelters` – ShelterManagementPage
- `/admin/lost-found` – LostFoundModerationPage
- `/admin/analytics` – PlatformAnalyticsPage

### ⚙️ 9. System

- `/notifications` – NotificationsPage
- `/settings` – SettingsPage
- `*` – NotFoundPage
