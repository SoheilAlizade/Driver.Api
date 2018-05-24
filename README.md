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
| `key`         |    65465465     |       |

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
    "PayAtOrigin": false
  }
}
```

| فیلد        |      مقدار      |                       توضیح                       |
| ----------- | :-------------: | :-----------------------------------------------: |
| `HasDriver` | true \|\| false | آیا بسته مورد نظر توسط راننده دیگر دریافت شده است |
| `Pack`      |      ----       |                    جزئیات بسته                    |

<h3>Pack</h3>

| فیلد          |      مقدار      |    توضیح     |
| ------------- | :-------------: | :----------: |
| `Origin`      |   تهران، ...    |  مبدا بسته   |
| `Destination` |    تهران...     |  مقصد بسته   |
| `Weight`      |     10 کیلو     |   وزن بسته   |
| `Type`        |       سبک       | وضعیت راننده |
| `PackCount`   |        5        | وضعیت راننده |
| `IsPacking`   | true \|\| false | وضعیت راننده |
| `IsInsurance` | true \|\| flase | وضعیت راننده |
| `Explain`     |  بسته شامل ..   | وضعیت راننده |
| `Price`       |       564       | وضعیت راننده |
| `PayAtOrigin` | true \|\| false | وضعیت راننده |
