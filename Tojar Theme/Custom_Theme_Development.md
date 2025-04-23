# شرح تصميم قالب جديد للتجار

**مسار الثيمات و قوالب التجار**
/www/wwwroot/xxxxx.com/core/resources/views/themes

# كيفية تصميم قالب جديد
يمكنك تصميم قالب جديد بناءا على الخطوات التالية او نسخ أحد القوالب و إجراء التغييرات به .

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
