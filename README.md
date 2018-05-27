# Driver Api

<div dir='rtl'>
<h2>
صفحه اول - خانه
</h2>
</div>

 <h3>URL</h3>

```
GET /api/v{version}/driver/status
```

 <h3>Response</h3>

```
{
 "Status": "string",
 "PackCount": 0,
 "Packs": [
   {
     "Origin": "string",
     "Destination": "string",
     "Weight": "string",
     "Type": "string",
     "PackCount": "string",
     "key": 0
   }
 ]
}
```

 <h3>Example</h3>

```
{
 "Status": "ready",
 "PackCount": 1,
 "Packs": [
   {
     "Origin": " استان string شهر string خیابان string کوچه string پلاک string طبقه string",
     "Destination": " استان string شهر string خیابان string کوچه string پلاک string طبقه string",
     "Weight": "بین 100 تا 200 کیلو گرم",
     "Type": "سبک",
     "PackCount": "5",
     "key": 3
   }
 ]
}
```

| فیلد        |       مقدار        |          توضیح           |
| ----------- | :----------------: | :----------------------: |
| `Status`    | ready \|\| resting |       وضعیت راننده       |
| `PackCount` |     1 ... 100+     | تعداد بسته های در انتظار |
| `Packs`     |       -----        | لیست بسته های در انتظار  |

<h4> Packs </h4>

| فیلد          |      مقدار      | توضیح |
| ------------- | :-------------: | :---: |
| `Origin`      | تهران،کوچه فلان |       |
| `Destination` | تهران،کوچه فلان |       |
| `Weight`      |   کیلو گرم 3    |       |
| `Type`        |       سبک       |       |
| `PackCount`   |        6        |       |
| `key`         |    65465465     |     کد سفارش  |

<div dir='rtl'>
در صفحه اول موبایل یعنی خانه برای دریافت وضعیت کاربر به همراه لیست سفارش ها می توان از این آدرس استفاده کنید
</div>

<hr>

<h2 dir='rtl'>
بروز رسانی وضعیت کاربر
</h2>

<p dir='rtl'>
برای بروز رسانی وضعیت کاربر از آدرس زیر استفاده کنید. این آدرس هیچ پارامتری دریافت نمی کند تنها لازم است درخواست را به آن ارسال کنید تا وضعیت کاربر به روز شود.
</p>

 <h3>URL</h3>

```
PUT /api/v{version}/driver/state
```

<h3> Response </h3>

_status code 200 - ok_

```
{
  "status_code": 200,
  "message": "Request been successfully.",
  "isSuccess": true
}
```

<hr>

<h1 dir='rtl'>
انتخاب بسته درس لیست انتظار
</h1>

<h3>
URL
</h3>

```
GET /api/v{version}/driver/pack/{key}
```

<h3> Response </h3>

_status code 200 - ok_

```
{
  "HasDriver": false,
  "Pack": {
    "Origin": " استان string شهر string خیابان string کوچه string پلاک string طبقه string",
    "Destination": " استان string شهر string خیابان string کوچه string پلاک string طبقه string",
    "Weight": "بین 100 تا 200 کیلو گرم",
    "Type": "سبک",
    "PackCount": "0",
    "IsPacking": true,
    "IsInsurance": true,
    "InsuranceValue": "",
    "Explain": "توضیح",
    "Price": 389512569,
    "PayAtOrigin": false,
    "key": 1
  }
}
```

| فیلد        |      مقدار      |                       توضیح                       |
| ----------- | :-------------: | :-----------------------------------------------: |
| `HasDriver` | true \|\| false | آیا بسته مورد نظر توسط راننده دیگر دریافت شده است |
| `Pack`      |      ----       |                    جزئیات بسته                    |

<h3>Pack</h3>

| فیلد          |      مقدار      |     توضیح      |
| ------------- | :-------------: | :------------: |
| `Origin`      |   تهران، ...    |   مبدا بسته    |
| `Destination` |    تهران...     |   مقصد بسته    |
| `Weight`      |     10 کیلو     |    وزن بسته    |
| `Type`        |       سبک       |  وضعیت راننده  |
| `PackCount`   |        5        |   تعداد بسته   |
| `IsPacking`   | true \|\| false |   بسته بندی    |
| `IsInsurance` | true \|\| flase |      بیمه      |
| `Explain`     |  بسته شامل ..   |    توضیحات     |
| `Price`       |       564       |      قیمت      |
| `PayAtOrigin` | true \|\| false | پرداخت در مقصد |

<div dir='rtl'>
توسط فیلد `HasDriver` میتوان بررسی کنید که آیا این بسته توسط راننده دیگر دریافت شده است یا خیر.
 </div>

<hr>

<h2 dir='rtl'>دریافت اطلاعات کامل بسته </h2>

<h3>URL</h3>

```
GET /api/v{version}/driver/pack/{key}/full
```

<h3>Response</h3>

_status code 200 - ok_

```
{
{
  "DisplayName": "string string",
  "PhoneNumber": "09198143732",
  "Destination": {
    "phone_number": "string",
    "reciver_name": "string",
    "address": " استان string شهر string خیابان string کوچه string پلاک string طبقه string",
    "province": "string",
    "city": "string",
    "street": "string",
    "plaque": "string",
    "latitude": "string",
    "longitude": "string",
    "floor": "string",
    "alley": "string",
    "key": 1
  },
  "Origin": {
    "address": " استان string شهر string خیابان string کوچه string پلاک string طبقه string",
    "province": "string",
    "city": "string",
    "street": "string",
    "plaque": "string",
    "latitude": "string",
    "longitude": "string",
    "floor": "string",
    "alley": "string",
    "key": 1
  },
  "Type": "سبک",
  "PackCount": "0",
  "IsPacking": true,
  "IsInsurance": true,
  "InsuranceValue": "بین 100 تا 200 میلیون تومان",
  "Location": "asdasd",
  "Explain": "توضیحات",
  "key": 1
}
```

<hr>

<h2 dir='rtl'>پذیرش درخواست </h2>

<h3>URL</h3>

```
PUT /api/v{version}/driver/pack/{key}/accept
```

<h3>Response</h3>
_status code 200 - ok_

```
{
  "status_code": 200,
  "message": "Request been successfully.",
  "isSuccess": true
}
```

<hr>

<h2 dir='rtl'>لغو درخواست </h2>

<h3>URL</h3>

```
PUT /api/v{version}/driver/pack/cancel
```

<h3>Request Body</h3>

```
{
  "Key": 0,
  "Description": "string"
}
```

| فیلد          | مقدار |      توضیح       |
| ------------- | :---: | :--------------: |
| `Key`         |   -   |      کدبسته      |
| `Description` |   -   | توضیحات برای لغو |

<h3>Response</h3>

```
{
  "status_code": 200,
  "message": "Request been successfully.",
  "isSuccess": true
}
```

<hr>

<h2 dir='rtl'>در مقصد هستم </h2>

<h3>URL</h3>

```
POST /api/v{version}/driver/pack/{key}/location-report
```

<h3>Response</h3>

```
{
  "status_code": 200,
  "message": "Request been successfully.",
  "isSuccess": true
}
```

<hr>

<h2 dir='rtl'> ویرایش جزئیات بسته</h2>

<h3>URL</h3>

```
PUT /api/v{version}/driver/pack/details
```

<h3>Request Body</h3>

```
{
  "PackTypeId": 0,
  "WeightId": 0,
  "IsInsurance": true,
  "InsuranceValueId": 0,
  "IsPacking": true,
  "PackCount": 0,
  "PayAtOrigin": true,
  "key": 0
}
```

<h3>Response</h3>

```
{
  "status_code": 200,
  "message": "Request been successfully.",
  "isSuccess": true
}
```

<hr>

<h2 dir='rtl'>تکمیل اسناد   </h2>

<h3>URL</h3>

```
PUT /api/v{version}/driver/pack/compelete
```

<h3>Request Body</h3>

```
{
  "NationalCodeBase64": "string",
  "PackBase64": "string",
  "SignatureBase64": "string",
  "key": 0
}
```

| فیلد                 | مقدار |    توضیح     |
| -------------------- | :---: | :----------: |
| `NationalCodeBase64` |   -   | عکس کارت ملی |
| `PackBase64`         |   -   |   عکس بسته   |
| `SignatureBase64`    |   -   |  تصویر امضا  |
| `key`                |   -   |   کد بسته    |

<h3>Response</h3>

```
{
  "status_code": 200,
  "message": "Request been successfully.",
  "isSuccess": true
}
```

<hr>

<h2 dir='rtl'>تحویل به پورت    </h2>

<h3>URL</h3>

```
PUT /api/v{version}/driver/pack/{key}/delivered
```

<h3>Response</h3>

```
{
  "status_code": 200,
  "message": "Request been successfully.",
  "isSuccess": true
}
```

<hr>

<h2 dir='rtl'>
پروفایل - منو
 </h2>

<h3>URL</h3>

```
GET /api/v{version}/driver/profile
```

<h3>Response</h3>

```
{
  "Code": 0,
  "DisplayName": "string",
  "PhotoUrl": "string"
}
```

<hr>

<h2 dir='rtl'>
پروفایل - کامل
 </h2>

<h3>URL</h3>

```
GET /api/v{version}/driver/profile/full
```

<h3>Response</h3>

```
{
  "Code": "string",
  "PhotoUrl": "string",
  "Status": "string",
  "FirstName": "string",
  "LastName": "string",
  "Gender": "string",
  "Vehicle": "string",
  "VehicleModel": "string",
  "VehiclePlaque": "string",
  "VehicleColor": "string",
  "PhoneNumber": "string",
  "Address": "string"
}
```

| فیلد            |       مقدار        |    توضیح     |
| --------------- | :----------------: | :----------: |
| `Code`          |         -          |      کد      |
| `PhotoUrl`      |         -          |   آدرس عکس   |
| `Status`        | ready \|\| resting | وضعیت راننده |
| `FirstName`     |         -          |     نام      |
| `LastName`      |         -          | نام خانوادگی |
| `Gender`        |         -          |    جنسیت     |
| `Vehicle`       |         -          |  نوع وسیله   |
| `VehicleModel`  |         -          |  مدل وسیله   |
| `VehiclePlaque` |         -          |  پلاک وسیله  |
| `VehicleColor`  |         -          |  رنگ وسیله   |
| `PhoneNumber`   |         -          |  شماره تلفن  |
| `Address`       |         -          |     آدرس     |

<hr>

<h2 dir='rtl'>
پیام ها
 </h2>

<h3>URL</h3>

```
GET  /api/v{version}/driver/messages
```

<h3>Response</h3>

```
[
  {
    "Message": "string",
    "CreatedOn": "string"
  }
]
```

<hr>

<h2 dir='rtl'>
تاریخچه
 </h2>

<h3>URL</h3>

```
GET /api/v{version}/driver/histories
```

<h3>Response</h3>

```
[
  {
    "Origin": "string",
    "Destination": "string",
    "Price": 0,
    "Code": "string",
    "Status": "string",
    "CreatedOn": "string"
  }
]
```

<hr>

<h2 dir='rtl'>
 جستجو تاریخچه
 </h2>

<h3>URL</h3>

```
GET /api/v{version}/driver/histories/search ?text="searchworkd"
```

<h3>Response</h3>

```
[
  {
    "Origin": "string",
    "Destination": "string",
    "Price": 0,
    "Code": "string",
    "Status": "string",
    "CreatedOn": "string"
  }
]
```
