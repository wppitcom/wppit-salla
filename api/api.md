# Salla API

**الملفات المسئولة هنا**

/www/wwwroot/domain.com/core/routes/api.php

```
<?php
//
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Route;
use App\Http\Controllers\Tenant\API\UserController;
use Modules\MobileApp\Http\Controllers\Api\V1\CategoryController;
use Modules\MobileApp\Http\Controllers\Api\V1\ChildCategoryController;
use Modules\MobileApp\Http\Controllers\Api\V1\CountryController;
use Modules\MobileApp\Http\Controllers\Api\V1\LanguageController;
use Modules\MobileApp\Http\Controllers\Api\V1\MobileSliderController;
use Modules\MobileApp\Http\Controllers\Api\V1\SiteSettingsController;
use Modules\MobileApp\Http\Controllers\Api\V1\SubCategoryController;
use Modules\MobileApp\Http\Controllers\CampaignController;
use Modules\MobileApp\Http\Controllers\FeaturedProductController;
use Modules\MobileApp\Http\Controllers\MobileController;
use Modules\MobileApp\Http\Controllers\ProductController;
use Stancl\Tenancy\Middleware\InitializeTenancyByDomain;
use Stancl\Tenancy\Middleware\PreventAccessFromCentralDomains;

/*
|--------------------------------------------------------------------------
| API Routes
|--------------------------------------------------------------------------
|
| Here is where you can register API routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| is assigned the "api" middleware group. Enjoy building your API!
|
*/
#reserverd for landlord api
/*----------------------------------------------------------------------
    API ROUTES FOR  TENANT ADMIN DASHBOARD SETTINGS
-----------------------------------------------------------------------*/


// Search solution from tenency package creator documentation
Route::middleware(['api'])->group(function () {
    Route::get('test', function (){
        return response('data', 200);
    });


    Route::prefix("v1")->group(function () {

        Route::post('/register',[UserController::class,'register']);
        Route::post('/login',[UserController::class,'login']);
        Route::post('social/login',[UserController::class,'socialLogin']);
        Route::get('/country',[CountryController::class,'country']);
        Route::get('/state/{country_id}',[CountryController::class,'stateByCountryId']);
        Route::post('/send-otp-in-mail',[UserController::class,'sendOTP']);
        Route::post('/otp-success',[UserController::class,'sendOTPSuccess']);
        Route::post('/reset-password',[UserController::class,'resetPassword']);
//Route::post('change-password', [UserController::class,'changePassword']);

        /*
         * todo:: all category route are below this line
         * */

        /* category */
        Route::group(['prefix' => 'category'],function(){
            Route::get('/',[CategoryController::class,'allCategory']);
            Route::get('/{id}',[CategoryController::class,'singleCategory']);
        });
        /* sub category */
        Route::group(['prefix' => 'subcategory'],function(){
            Route::get('/{country_id}',[SubCategoryController::class,'allSubCategory']);
            Route::get('/{country_id}/{id}',[SubCategoryController::class,'singleSubCategory']);
        });
        /* sub category */
        Route::group(['prefix' => 'child-category'],function(){
            Route::get('/{sub_category}',[ChildCategoryController::class,'allChildCategory']);
            Route::get('/{sub_category}/{id}',[ChildCategoryController::class,'singleChildCategory']);
        });

        Route::get("all-categories", [CategoryController::class,"allCategories"]);
        /*
         * todo:: all type of category route ends
         * */

        /*
         * todo:: all type of products route starts
         * */


// Product Route
// Fetch feature product
        Route::get("featured/product", [FeaturedProductController::class,'index']);
        Route::get("campaign/product/{id?}", [FeaturedProductController::class,'campaign']);
        Route::get("campaign", [CampaignController::class,'index']); // done
        Route::get("product", [ProductController::class,'search'])->name("api.products.search");
        Route::get("product/{id}", [ProductController::class,'productDetail']);
        Route::get("product/price-range", [ProductController::class,'priceRange']);
        Route::post("product-review", [ProductController::class,'storeReview']);
        Route::post('/category/{id}',[ProductController::class,'singleProducts']);
        Route::post('/subcategory/{id}',[ProductController::class,'singleProducts']);
        Route::get('/search-items',[ProductController::class,'searchItems']);
        Route::get('terms-and-condition-page', [MobileController::class, 'termsAndCondition']);
        Route::get('privacy-policy-page', [MobileController::class, 'privacyPolicy']);
        Route::get('site_currency_symbol', [MobileController::class, 'site_currency_symbol']);
        Route::get('/language',[LanguageController::class,'languageInfo']);
        Route::post('/translate-string',[LanguageController::class,'translateString']);
        /*
         * todo:: all type of products route ends
         * */
        Route::get('/mobile-slider/{type}',[MobileSliderController::class,"index"]);
        Route::get('/mobile-intro',[MobileIntroApiController::class,"mobileIntro"]);


        Route::get("/payment-gateway-list",[SiteSettingsController::class,"payment_gateway_list"]);

        Route::group(['prefix' => 'user/','middleware' => 'auth:sanctum'],function (){
            Route::post('logout',[UserController::class,'logout']);
            Route::get('profile',[UserController::class,'profile']);

            Route::post('change-password',[UserController::class,'changePassword']);
            Route::post('update-profile',[UserController::class,'updateProfile']);
            Route::group(['prefix' => 'support-tickets'],function(){
                Route::post('/',[UserController::class,'allTickets']);
                Route::post('/{id}',[UserController::class,'viewTickets']);
            });

            /* Add shipping method */
            Route::get("/all-shipping-address",[UserController::class,"get_all_shipping_address"]);
            Route::get("/shipping-address/delete/{shipping}",[UserController::class,"delete_shipping_address"]);
            Route::post("/add-shipping-address",[UserController::class,"storeShippingAddress"]);
            Route::get("/get-department",[UserController::class,"get_department"]);
            Route::get("ticket",[UserController::class,"get_all_tickets"]);
            Route::get("ticket/{id}",[UserController::class,"single_ticket"]);
            Route::get("ticket/chat/{ticket_id}",[UserController::class,"fetch_support_chat"]);
            Route::post("ticket/chat/send/{ticket_id}",[UserController::class,"send_support_chat"]);
            Route::post('ticket/message-send',[UserController::class,'sendMessage']);
            Route::post('ticket/create',[UserController::class,'createTicket']);
            Route::post('ticket/priority-change', [UserController::class,'priority_change']);
            Route::post('ticket/status-change', [UserController::class,'status_change']);

        });
    });

    Route::post('/register', [UserController::class, 'register']);
    Route::post('/login', [UserController::class, 'login']);
});


// todo:: this route will execute if no route matched
Route::fallback(function (){
    return response()->json(['msg' => __('page not found')],404);
});


```


