# شرح تصميم قالب جديد للتجار

**مسار الثيمات و قوالب التجار**
/www/wwwroot/xxxxx.com/core/resources/views/themes

# كيفية تصميم قالب جديد
يمكنك تصميم قالب جديد بناءا على الخطوات التالية او نسخ أحد القوالب و إجراء التغييرات به .

[تحميل قالب جاهز كمثال يسهل التعديل عليه](https://www.wppit.com/WP-shop-File/raqmnah.zip)


**عند الدخول الى مجلد القوالب قم بإنشاء مجلد للقالب الجديد - يجب أن يحتوي مجلد القالب الجديد على ملف JSON باسم theme.json كما يلي:**

وفرنا theme.json يمكنك نسخه من خلال مجلد Tojar theme فى Github

** شرح كود ملف theme.json **


```json
{
    "name": "Theme Name",
    "slug": "theme_slug",
    "description": "Your Theme Description",
    "author": "Your Theme Author Name",
    "version": "1.0.0",
    "status": true,
    "screenshot": [
        {
            "primary": "primary.jpg",
            "sort": "desc"
        }
    ],
    "headerHook": [
        {
            "loadCoreStyle": {
                "odometer": false,
                "common": false,
                "magnific-popup": false
            },
            "style": ["your_theme_css"],
            "rtl_style": ["rtl"],
            "script": [],
            "blade": [],
            "navbarArea": "navbar",
            "breadcrumbArea": "breadcrumb"
        }
    ],
    "footerHook": [
        {
            "loadCoreScript": {
                "odometer": false,
                "viewport.jquery": false,
                "main": false
            },
            "style": [],
            "script": ["custom_script", "main"],
            "blade": [],
            "widgetArea": "footer"
        }
    ]
}
```

## 🧩 شرح إعدادات ملف theme.json

يحتوي هذا الملف على معلومات تعريفية وإعدادات أساسية لأي قالب مخصص داخل المنصة. يجب الالتزام بالهيكل التالي لضمان عمل القالب بشكل سليم.

**صورة مجلدات القالب**

<p align="center">
  <img src="https://www.wppit.com/wp-content/uploads/2025/04/ice_screenshot_٢٠٢٥٠٤٢٣-١٩٠٣٠٢.jpeg" width="60%" />
</p>


---

### 🏷️ slug

- **يجب أن يكون فريدًا** ولا يتكرر.
- يجب أن **يتطابق تمامًا** مع اسم مجلد القالب المخصص.

---

### ✅ status

- قيمة منطقية (Boolean):  
  - `true` لتفعيل القالب.  
  - `false` لتعطيله.

---

### 🖼️ screenshot

- يحتوي على صورة المعاينة الخاصة بالقالب.
- **`primary`**: اسم ملف الصورة (jpg, jpeg, png فقط).  
  - سيتم استخدامها كصورة رئيسية لمعاينة القالب.

---

### 🔼 headerHook

تُستخدم هذه الخاصية لتحديد الملفات التي سيتم تحميلها داخل رأس الصفحة (head).

#### `loadCoreStyle`
- تقبل أسماء ملفات CSS (بدون الامتداد).
- يمكنك تعطيل تحميل ملفات CSS الأساسية من النظام بوضع `false`.

#### `style`
- مصفوفة تحتوي على أسماء ملفات CSS الخاصة بالقالب.
- **المسار**:  
  `yourThemeDirectory/assets/css`

#### `script`
- مصفوفة تحتوي على ملفات JavaScript المراد تحميلها في رأس الصفحة.
- **المسار**:  
  `yourThemeDirectory/assets/js`

#### `blade`
- مصفوفة تحتوي على أسماء ملفات Blade التي سيتم عرضها بعد الـ Navbar والـ Breadcrumb.
- **المسار**:  
  `yourThemeDirectory/headerHookTemplate`

#### `navbarArea`
- اسم ملف الـ Blade الخاص بشريط التنقل (Navbar).
- **المسار**:  
  `yourThemeDirectory/headerNavbarArea`

#### `breadcrumbArea`
- اسم ملف الـ Blade الخاص بشريط التصفح (Breadcrumb).
- **المسار**:  
  `yourThemeDirectory/headerBreadcrumbArea`

---

### 🔽 footerHook

تُستخدم لتحديد الملفات التي سيتم تحميلها داخل تذييل الصفحة (footer).

#### `loadCoreScript`
- تقبل أسماء ملفات JavaScript من النظام الأساسي.
- ضع `false` لتعطيل تحميل ملف معين، أو `true` لتحميله.

#### `style`
- ملفات CSS تُحمّل في نهاية الصفحة.
- **المسار**:  
  `yourThemeDirectory/assets/css`

#### `script`
- ملفات JavaScript تُحمّل في نهاية الصفحة.
- **المسار**:  
  `yourThemeDirectory/assets/js`

#### `blade`
- ملفات Blade يتم عرضها باستخدام دالة `renderFooterHookBladeFile()`.
- **المسار**:  
  `yourThemeDirectory/footerHookTemplate`

#### `widgetArea`
- اسم ملف Blade الخاص بمنطقة الودجت في التذييل.
- **المسار**:  
  `yourThemeDirectory/footerWidgetArea`

---

📝 **ملاحظات مهمة**:

- تأكد من صحة أسماء الملفات والامتدادات.
- احرص على أن تكون كل المسارات والملفات متوافقة مع بنية مجلد القالب الخاص بك.
- يُفضل مراجعة نموذج `theme.json` المرفق لفهم الهيكل بشكل عملي.

