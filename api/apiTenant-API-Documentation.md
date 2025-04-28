# مسار الملف 
/www/wwwroot/domain.com/core/routes/tenant_api.php

# Tenant API Documentation

This document provides the details for the Tenant API in version 1.0.

## Base URL
/www/wwwroot/domain.com/core/routes/tenant_api.php

# API Documentation

## 1. **المصادقة والتسجيل**

| Method | Endpoint                   | Description                     |
|--------|----------------------------|---------------------------------|
| POST   | /register                   | تسجيل مستخدم جديد               |
| POST   | /username                   | التحقق من اسم المستخدم          |
| POST   | /login                      | تسجيل الدخول                    |
| POST   | /social/login               | تسجيل الدخول عبر الشبكات الاجتماعية |

## 2. **البلدان والمناطق**

| Method | Endpoint                        | Description                             |
|--------|---------------------------------|-----------------------------------------|
| GET    | /country                        | استرجاع قائمة البلدان                  |
| GET    | /state/{country_id}             | استرجاع قائمة الولايات من خلال البلد  |
| GET    | /city/{state_id}                | استرجاع قائمة المدن من خلال الولاية  |
| GET    | /search/country/{name}          | البحث عن بلد معين                      |
| GET    | /search/state/{name}            | البحث عن ولاية معينة                   |
| GET    | /search/city/{id}/{name}        | البحث عن مدينة معينة                   |

## 3. **إرسال واستلام OTP**

| Method | Endpoint                        | Description                             |
|--------|---------------------------------|-----------------------------------------|
| POST   | /send-otp-in-mail              | إرسال رمز OTP عبر البريد الإلكتروني    |
| POST   | /otp-success                    | التحقق من نجاح OTP                      |
| POST   | /reset-password                 | إعادة تعيين كلمة المرور                |

## 4. **الفئات والمنتجات**

### الفئات

| Method | Endpoint        | Description                 |
|--------|-----------------|-----------------------------|
| GET    | /category       | استرجاع قائمة الفئات        |
| GET    | /category/{id}  | استرجاع تفاصيل فئة معينة   |

### المنتجات

| Method | Endpoint        | Description                 |
|--------|-----------------|-----------------------------|
| GET    | /product        | استرجاع قائمة المنتجات     |
| GET    | /product/{id}   | استرجاع تفاصيل منتج معين   |
| POST   | /product-review | إرسال تقييم لمنتج          |

## 5. **الدعم الفني**

| Method | Endpoint                         | Description                          |
|--------|----------------------------------|--------------------------------------|
| POST   | /user/support-tickets/           | استرجاع جميع التذاكر الخاصة بالمستخدم |
| POST   | /user/support-tickets/{id}       | استرجاع تفاصيل تذكرة معينة         |

## 6. **المنتجات المميزة**

| Method | Endpoint                         | Description                          |
|--------|----------------------------------|--------------------------------------|
| GET    | /featured/product/{limit?}        | استرجاع المنتجات المميزة            |
| GET    | /recent/product/{limit?}          | استرجاع المنتجات الحديثة            |
| GET    | /campaign/product/{id?}           | استرجاع المنتجات من الحملة          |

## 7. **المستخدم والحساب**

### إدارة الحساب

| Method | Endpoint                     | Description                           |
|--------|------------------------------|---------------------------------------|
| POST   | /user/logout                 | تسجيل الخروج                         |
| GET    | /user/profile                | استرجاع معلومات الملف الشخصي        |
| POST   | /user/change-password        | تغيير كلمة المرور                   |
| POST   | /user/update-profile         | تحديث الملف الشخصي                  |

### التذاكر والدعم

| Method | Endpoint                         | Description                          |
|--------|----------------------------------|--------------------------------------|
| POST   | /user/support-tickets/           | استرجاع جميع التذاكر الخاصة بالمستخدم |
| POST   | /user/support-tickets/{id}       | استرجاع تفاصيل تذكرة معينة         |

## 8. **الإعدادات والصفحات**

| Method | Endpoint                       | Description                           |
|--------|--------------------------------|---------------------------------------|
| GET    | /terms-and-condition-page      | استرجاع صفحة الشروط والأحكام         |
| GET    | /privacy-policy-page           | استرجاع صفحة سياسة الخصوصية         |

## 9. **إعدادات اللغة والعملات**

| Method | Endpoint                       | Description                           |
|--------|--------------------------------|---------------------------------------|
| GET    | /language                      | استرجاع معلومات اللغة               |
| POST   | /translate-string              | ترجمة السلاسل النصية                |
| GET    | /site-currency-symbol          | استرجاع رمز العملة للموقع           |

## 10. **طرق الدفع والشحن**

| Method | Endpoint                       | Description                           |
|--------|--------------------------------|---------------------------------------|
| GET    | /payment-gateway-list          | استرجاع قائمة بوابات الدفع          |
| POST   | /coupon                        | استرجاع رمز الكوبون الخاص بالمنتج    |
| POST   | /shipping-charge               | استرجاع رسوم الشحن                   |

---

**ملاحظة:**  
هذا التوثيق يتم تحديثه بشكل دوري ويحتوي على جميع النقاط المتعلقة بنقاط النهاية المختلفة، وقد يتم إضافة أو تعديل بعض النقاط حسب التغييرات التي تطرأ على التطبيق.
