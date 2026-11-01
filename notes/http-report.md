# HTTP Exploration Report

## 1. Introduction

اداة **curl** هي أداة command-line تستخدم لنقل البيانات عبر الشبكة، وتعتمد على بروتوكولات متعددة أهمها HTTP و HTTPS.
سنستخدم في هذا التمرين DummyJSON لأنها توفر ميزة مفيدة يمكننا طلب استجابة برمز `400` أو `404` بشكل مقصود، مع جسم JSON.
امر تشعيل الاداة : `curl.exe url`

## 2. Successful GET Request (200)

سننفذ طلب جلب للبيانات طلب (GET) للحصول على منتج.
حالة الاستجابة HTTP/1.1 200 OK تعني أن الطلب تم بنجاح تام ولا توجد أي أخطاء.
الأمر المنفذ:

```
C:\Users\ASUS> curl.exe -i -X GET "https://dummyjson.com/products/1"
```

### Request

- Method: GET
- URL: https://dummyjson.com/products/1

### Response

```http
HTTP/1.1 200 OK
Date: Sun, 01 Nov 2026 09:06:23 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
access-control-allow-credentials: true
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=cYeN6HZPlJhLIL0KPiyLVKAbZwiwLq1fLFidTBrXuKXNXS4kK%2BmNh8vBK%2BZE7AiQ1aJ%2FZ1Y44eGiE4Nxg2Oy2RBmvDWg%2FL%2FXKZJIo6sPfXE1fFG22HepDjTuSvDomGqn"}]}
etag: W/"5e6-LuZgXJ6APIKHswyRKC9GQ6dxUNE"
strict-transport-security: max-age=15552000; includeSubDomains
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-dns-prefetch-control: off
x-download-options: noopen
x-frame-options: SAMEORIGIN
x-ratelimit-limit: 100
x-ratelimit-remaining: 99
x-ratelimit-reset: 1792074538
x-xss-protection: 1; mode=block
Age: 164984
Cache-Control: no-store
cf-cache-status: HIT
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Server: cloudflare
CF-RAY: a539be3edc59baaf-MXP

{"id":1,"title":"Essence Mascara Lash Princess","description":"The Essence Mascara Lash Princess is a popular mascara known for its volumizing and lengthening effects. Achieve dramatic lashes with this long-lasting and cruelty-free formula.","category":"beauty","price":9.99,"discountPercentage":10.48,"rating":2.56,"stock":99,"tags":["beauty","mascara"],"brand":"Essence","sku":"BEA-ESS-ESS-001","weight":4,"dimensions":{"width":15.14,"height":13.08,"depth":22.99},"warrantyInformation":"1 week warranty","shippingInformation":"Ships in 3-5 business days","availabilityStatus":"In Stock","reviews":[{"rating":3,"comment":"Would not recommend!","date":"2025-04-30T09:41:02.053Z","reviewerName":"Eleanor Collins","reviewerEmail":"eleanor.collins@x.dummyjson.com"},{"rating":4,"comment":"Very satisfied!","date":"2025-04-30T09:41:02.053Z","reviewerName":"Lucas Gordon","reviewerEmail":"lucas.gordon@x.dummyjson.com"},{"rating":5,"comment":"Highly impressed!","date":"2025-04-30T09:41:02.053Z","reviewerName":"Eleanor Collins","reviewerEmail":"eleanor.collins@x.dummyjson.com"}],"returnPolicy":"No return policy","minimumOrderQuantity":48,"meta":{"createdAt":"2025-10-09T14:47:01.588Z","updatedAt":"2026-05-23T11:27:41.868Z","barcode":"5784719087687","qrCode":"https://cdn.dummyjson.com/public/qr-code.png"},"images":["https://cdn.dummyjson.com/product-images/beauty/essence-mascara-lash-princess/1.webp"],"thumbnail":"https://cdn.dummyjson.com/product-images/beauty/essence-mascara-lash-princess/thumbnail.webp"}
```

- Status Code: 200 , massage :OK
  الخادم جلب لي البيانات بنجاح.
- Content-Type: application/json; charset=utf-8
  البيانات بصيقة `json` اي نوع البيانات الموجودة في جسم الاستجابة.
- Response Headers:
  هو الجزء الذي يحتوي على معلومات وصفية (Metadata) حول الخادم، نوع البيانات، الأمان، والتحكم بالتخزين المؤقت (Cache).

```http
Date: Sun, 01 Nov 2026 09:06:23 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
access-control-allow-credentials: true
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=cYeN6HZPlJhLIL0KPiyLVKAbZwiwLq1fLFidTBrXuKXNXS4kK%2BmNh8vBK%2BZE7AiQ1aJ%2FZ1Y44eGiE4Nxg2Oy2RBmvDWg%2FL%2FXKZJIo6sPfXE1fFG22HepDjTuSvDomGqn"}]}
etag: W/"5e6-LuZgXJ6APIKHswyRKC9GQ6dxUNE"
strict-transport-security: max-age=15552000; includeSubDomains
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-dns-prefetch-control: off
x-download-options: noopen
x-frame-options: SAMEORIGIN
x-ratelimit-limit: 100
x-ratelimit-remaining: 99
x-ratelimit-reset: 1792074538
x-xss-protection: 1; mode=block
Age: 164984
Cache-Control: no-store
cf-cache-status: HIT
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Server: cloudflare
CF-RAY: a539be3edc59baaf-MXP
```

- Response Body:
  هو المحتوى الفعلي أو البيانات التي طلبها العميل (Client)

```json
{
  "id": 1,
  "title": "Essence Mascara Lash Princess",
  "description": "The Essence Mascara Lash Princess is a popular mascara known for its volumizing and lengthening effects. Achieve dramatic lashes with this long-lasting and cruelty-free formula.",
  "category": "beauty",
  "price": 9.99,
  "discountPercentage": 10.48,
  "rating": 2.56,
  "stock": 99,
  "tags": ["beauty", "mascara"],
  "brand": "Essence",
  "sku": "BEA-ESS-ESS-001",
  "weight": 4,
  "dimensions": {
    "width": 15.14,
    "height": 13.08,
    "depth": 22.99
  },
  "warrantyInformation": "1 week warranty",
  "shippingInformation": "Ships in 3-5 business days",
  "availabilityStatus": "In Stock",
  "reviews": [
    {
      "rating": 3,
      "comment": "Would not recommend!",
      "date": "2025-04-30T09:41:02.053Z",
      "reviewerName": "Eleanor Collins",
      "reviewerEmail": "eleanor.collins@x.dummyjson.com"
    },
    {
      "rating": 4,
      "comment": "Very satisfied!",
      "date": "2025-04-30T09:41:02.053Z",
      "reviewerName": "Lucas Gordon",
      "reviewerEmail": "lucas.gordon@x.dummyjson.com"
    },
    {
      "rating": 5,
      "comment": "Highly impressed!",
      "date": "2025-04-30T09:41:02.053Z",
      "reviewerName": "Eleanor Collins",
      "reviewerEmail": "eleanor.collins@x.dummyjson.com"
    }
  ],
  "returnPolicy": "No return policy",
  "minimumOrderQuantity": 48,
  "meta": {
    "createdAt": "2025-10-09T14:47:01.588Z",
    "updatedAt": "2026-05-23T11:27:41.868Z",
    "barcode": "5784719087687",
    "qrCode": "https://cdn.dummyjson.com/public/qr-code.png"
  },
  "images": [
    "https://cdn.dummyjson.com/product-images/beauty/essence-mascara-lash-princess/1.webp"
  ],
  "thumbnail": "https://cdn.dummyjson.com/product-images/beauty/essence-mascara-lash-princess/thumbnail.webp"
}
```

## 3. Client Error Response (400)

سننفذ الان طلب جلب للبانات ولكن الخادم سيعيد استجابة بحالة 400 Bad Request
نعني أن الخادم رفض الطلب أو لم يفهمه بسبب خطأ من قبل الـ (Client) مثل: بيانات ناقصة، صيغة JSON غير صحيحة، أو معلمات مفقودة في الطلب.

**ننوه** ان كود الخطأ `400 Bad Request` لا يقتصر على `GET` ولكن يمكن ان يظهر باي method اخرى مثل : (`POST`, `PUT`, `DELETE`, `PATCH`)

الامر المنفذ:

```
C:\Users\ASUS>curl.exe -i -X GET "https://dummyjson.com/http/400/Bad_Request"
```

### Request

- Method: GET
- URL:https://dummyjson.com/http/400/Bad_Request

### Response

```http
HTTP/1.1 400 Bad Request
Date: Sun, 01 Nov 2026 09:21:10 GMT
Content-Type: application/problem+json; charset=utf-8
Content-Length: 104
Connection: keep-alive
access-control-allow-credentials: true
etag: W/"68-lYQQP3057qtdleZpfnFOz71rqXo"
strict-transport-security: max-age=15552000; includeSubDomains
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-dns-prefetch-control: off
x-download-options: noopen
x-frame-options: SAMEORIGIN
x-ratelimit-limit: 100
x-ratelimit-remaining: 99
x-ratelimit-reset: 1793524877
x-xss-protection: 1; mode=block
cf-cache-status: DYNAMIC
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=m8BwGpHA6IBjrS%2Fe4hEiy0APG%2Bn9k9BZkvadE5EDVlvNYdclSu%2BlXJbHSSDarPlu3fsWWO1Pfmty5WOWdiFWzl0zEYMQMdAI1Y05iEESv9IMF9vnJrQjnyavTlLB6afL"}]}
Server: cloudflare
CF-RAY: a539d3e43d574c69-MXP
{"status":400,"title":"Bad_Request","type":"about:blank","detail":"Bad_Request","message":"Bad_Request"}
```

- Status Code: 400
- Content-Type: application/problem+json; charset=utf-8
- Response Headers:

```http
Date: Sun, 01 Nov 2026 09:21:10 GMT
Content-Type: application/problem+json; charset=utf-8
Content-Length: 104
Connection: keep-alive
access-control-allow-credentials: true
etag: W/"68-lYQQP3057qtdleZpfnFOz71rqXo"
strict-transport-security: max-age=15552000; includeSubDomains
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-dns-prefetch-control: off
x-download-options: noopen
x-frame-options: SAMEORIGIN
x-ratelimit-limit: 100
x-ratelimit-remaining: 99
x-ratelimit-reset: 1793524877
x-xss-protection: 1; mode=block
cf-cache-status: DYNAMIC
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=m8BwGpHA6IBjrS%2Fe4hEiy0APG%2Bn9k9BZkvadE5EDVlvNYdclSu%2BlXJbHSSDarPlu3fsWWO1Pfmty5WOWdiFWzl0zEYMQMdAI1Y05iEESv9IMF9vnJrQjnyavTlLB6afL"}]}
Server: cloudflare
CF-RAY: a539d3e43d574c69-MXP
```

- Response Body:

```
{"status":400,"title":"Bad_Request","type":"about:blank","detail":"Bad_Request","message":"Bad_Request"}
```

## 4. Not Found Response (404)

سننفذ الان طلب جلب للبانات ايضا ولكن الخادم سيعيد استجابة بحالة 404 Not Found
وهذه الحالة تعني أن الخادم استقبل الطلب بنجاح لكن المورد أو المسار المطلوب الذي نحاول الوصول إليه غير موجود، أو أن الخادم لا يوفره.
مثل: كتابة مسار خاطئ أو طلب منتج/مستخدم `id` غير موجود في قاعدة البيانات.

وايضا يمكن ان يظهر هذا الخطأ باي طريقة مثل : (`POST`, `PUT`, `DELETE`, `PATCH`)

الأمر المنفذ:

```
C:\Users\ASUS>curl.exe -i -X GET "https://dummyjson.com/http/404/Not_Found"
```

### Request

- Method: GET
- URL: https://dummyjson.com/http/404/Not_Found

### Response

```http
HTTP/1.1 404 Not Found
Date: Sun, 01 Nov 2026 09:34:22 GMT
Content-Type: application/problem+json; charset=utf-8
Content-Length: 98
Connection: keep-alive
access-control-allow-credentials: true
etag: W/"62-iEL9FCvs3Bv6MGwr5axpVY3VZMk"
strict-transport-security: max-age=15552000; includeSubDomains
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-dns-prefetch-control: off
x-download-options: noopen
x-frame-options: SAMEORIGIN
x-ratelimit-limit: 100
x-ratelimit-remaining: 99
x-ratelimit-reset: 1793525667
x-xss-protection: 1; mode=block
cf-cache-status: DYNAMIC
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=YkvZfLECH3wZnE2fkzkvNU34CbQe6%2BNZ9ZF1qpMvhVmWhE5OJF6rR3j2DWLzVnHhVAY9UGuCGJZcV1Bl4ZBQo5aJ6CXEb%2BfEu6QExU9b872EVe6XsraOIKvlBPnuFu%2BR"}]}
Server: cloudflare
CF-RAY: a539e73e3c03a01f-MXP

{"status":404,"title":"Not_Found","type":"about:blank","detail":"Not_Found","message":"Not_Found"}
```

- Status Code: 404

- Content-Type: application/problem+json; charset=utf-8

- Response Headers:

```http
Date: Sun, 01 Nov 2026 09:34:22 GMT
Content-Type: application/problem+json; charset=utf-8
Content-Length: 98
Connection: keep-alive
access-control-allow-credentials: true
etag: W/"62-iEL9FCvs3Bv6MGwr5axpVY3VZMk"
strict-transport-security: max-age=15552000; includeSubDomains
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-dns-prefetch-control: off
x-download-options: noopen
x-frame-options: SAMEORIGIN
x-ratelimit-limit: 100
x-ratelimit-remaining: 99
x-ratelimit-reset: 1793525667
x-xss-protection: 1; mode=block
cf-cache-status: DYNAMIC
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=YkvZfLECH3wZnE2fkzkvNU34CbQe6%2BNZ9ZF1qpMvhVmWhE5OJF6rR3j2DWLzVnHhVAY9UGuCGJZcV1Bl4ZBQo5aJ6CXEb%2BfEu6QExU9b872EVe6XsraOIKvlBPnuFu%2BR"}]}
Server: cloudflare
CF-RAY: a539e73e3c03a01f-MXP
```

- Response Body:

```json
{
  "status": 404,
  "title": "Not_Found",
  "type": "about:blank",
  "detail": "Not_Found",
  "message": "Not_Found"
}
```

## 5. Conclusion

تتكون أي استجابة من الخادم (Server Response) في الويب من ثلاثة أجزاء رئيسية:

1. **حالة الاستجابة (Status Line):** مثل `HTTP/1.1 200 OK` أو `400` أو `404`، وتحدد النتيجة العامة للطلب (نجاح أو نوع الخطأ).

2. **رأس الاستجابة (Response Headers):** مجموعة من البيانات الوصفية (Metadata) التي تخبر المتصفح أو التطبيق بكيفية التعامل مع البيانات (مثل `Content-Type` لتحديد نوع الملف، وعدد الطلبات المتبقية `Rate-Limit`).

3. **جسم الاستجابة (Response Body):** المحتوى الفعلي أو البيانات المطلوبة (Payload)، وغالباً ما يأتي بصيغة **JSON** سواء كان يحمل بيانات نجاح (مثل تفاصيل منتج) أو تفاصيل رسالة خطأ.

## What did I learn from this exercise?

بصراحة كانت تجربة ممتازة وغنية جداً. هذه المرة الأولى التي أتعامل فيها مع أداة `cURL` من الـ Command Line، وقدرت من خلال هذا التمرين أتعلم أساسيات جديدة وأطبقها بشكل عملي، مثل تنزيل المواقع،والتعامل مع API وغيرها من الأوامر.

الأكثر فائدة بالنسبة لي هو كيف ترسخت عندي مفاهيم طلبات واستجابات الـ HTTP بشكل أعمق لأنني كنت متعوداً على استخدام مكتبة Axios أو Fetch داخل الكود، أو الاعتماد على أداة مثل Postman لتجربة الـ API .
و التعامل المباشر من الترمينال جعلني أفهم بشكل أوضح كيف تنتقل الـ Headers والـ Status Codes والـ Body خلف الكواليس وبشكل مباشر، وكانت خطوة مفيدة لي على ما اعتقد.
