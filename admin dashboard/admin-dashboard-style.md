# التحكم فى قوائم لوحة التحكم و عناصرها 
**جميع الروابط تبدأ من المجلد الرئيسى باسم نطاقك فى سيرفرك  و كمثال**
إذا كان اسم موقعك  wppit.com فإن الملفات المشار اليها يجب ان تكون اسفل مجلد الرووت مباشرة و هو مجلد wppit.com
**للمساعدة تواصل مع support@wppit.com**

 # ملف مسئول عن تحسين التصميم باستخدام CSs&js&php فى لوحة تحكم الإدارة
\assets\common\css\custom-style.css

\assets\landlord\admin\js\misc.js

# ملف ترتيب القوائم 

core\app\Helpers\SidebarMenuHelper.php

**مثال من داخل الملف**

```private function tenant_payment_settings_menus(MenuWithPermission $menu_instance): void
    {
        $menu_instance->add_menu_item('payment-settings-menu-items', [
            'route' => '#',
            'label' => __('Payment Settings'),
            'parent' => null,
            'permissions' => ['paypal-payment-settings'],
            'icon' => 'mdi mdi-coin',
        ]);```
