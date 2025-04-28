# WPPiT  - API Documentation

This document describes the available API endpoints for the WPPit Salla Script  multi-vendor platform.

## Base URL


## Authentication
- Some endpoints require **Bearer Token** authentication via Laravel Sanctum.
- Login and Register endpoints are public.

---

## Endpoints

### Authentication

| Method | URL | Description |
|:------:|:---|:------------|
| POST | /register | Register a new user |
| POST | /login | Login user |
| POST | /social/login | Social login |
| POST | /send-otp-in-mail | Send OTP to user email |
| POST | /otp-success | Validate OTP |
| POST | /reset-password | Reset password |

---

### Categories

| Method | URL | Description |
|:------:|:---|:------------|
| GET | /category/ | List all categories |
| GET | /category/{id} | Get single category by ID |
| GET | /subcategory/{country_id} | List subcategories by country ID |
| GET | /subcategory/{country_id}/{id} | Get single subcategory |
| GET | /child-category/{sub_category} | List child categories |
| GET | /child-category/{sub_category}/{id} | Get single child category |
| GET | /all-categories | Get all categories in a flat list |

---

### Products

| Method | URL | Description |
|:------:|:---|:------------|
| GET | /featured/product | List featured products |
| GET | /campaign/product/{id?} | List products under a campaign |
| GET | /campaign | List all campaigns |
| GET | /product | Search products |
| GET | /product/{id} | Product detail |
| GET | /product/price-range | Get products price range |
| POST | /product-review | Submit product review |
| POST | /category/{id} | Products under a category |
| POST | /subcategory/{id} | Products under a subcategory |
| GET | /search-items | Search items |

---

### Site Info

| Method | URL | Description |
|:------:|:---|:------------|
| GET | /terms-and-condition-page | Terms and Conditions |
| GET | /privacy-policy-page | Privacy Policy |
| GET | /site_currency_symbol | Get the site currency symbol |

---

### Language

| Method | URL | Description |
|:------:|:---|:------------|
| GET | /language | List available languages |
| POST | /translate-string | Translate a given string |

---

### Mobile Features

| Method | URL | Description |
|:------:|:---|:------------|
| GET | /mobile-slider/{type} | List mobile sliders |
| GET | /mobile-intro | Get mobile intro content |

---

### Payment

| Method | URL | Description |
|:------:|:---|:------------|
| GET | /payment-gateway-list | List available payment gateways |

---

### Support Tickets (Authenticated)

**Requires Bearer Token**

| Method | URL | Description |
|:------:|:---|:------------|
| POST | /user/support-tickets/ | List all tickets |
| POST | /user/support-tickets/{id} | View a single ticket |
| GET | /user/ticket | Get all tickets |
| GET | /user/ticket/{id} | Get a ticket by ID |
| GET | /user/ticket/chat/{ticket_id} | Fetch support chat |
| POST | /user/ticket/chat/send/{ticket_id} | Send support chat message |
| POST | /user/ticket/message-send | Send new ticket message |
| POST | /user/ticket/create | Create a new support ticket |
| POST | /user/ticket/priority-change | Change ticket priority |
| POST | /user/ticket/status-change | Change ticket status |

---

### User Profile (Authenticated)

| Method | URL | Description |
|:------:|:---|:------------|
| POST | /user/logout | Logout |
| GET | /user/profile | Get user profile |
| POST | /user/change-password | Change user password |
| POST | /user/update-profile | Update user profile |
| GET | /user/all-shipping-address | Get all shipping addresses |
| GET | /user/shipping-address/delete/{shipping} | Delete a shipping address |
| POST | /user/add-shipping-address | Add a new shipping address |
| GET | /user/get-department | Get support departments |

---

## Error Handling

- If an endpoint is not found, the API will return a JSON:
```json
{
    "msg": "page not found"
}
