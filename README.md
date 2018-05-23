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

| توضیح       |      مقدار       |        فیلد           |
| ----------- | :---------------: | :----------------------: |
| `Status`    | `ready | resting` |       وضعیت راننده       |
| `PackCount` |    1 ... 100+     | تعداد بسته های در انتظار |
| `Packs`     |       -----       | لیست بسته های در انتظار  |

<h4> Packs </h4>

| توضیح         | مقدار | فیلد |
| ------------- | :---: | :--: |
| `Origin`      |       |      |
| `Destination` |       |      |
| `Packs`       |       |      |
| `Weight`      |       |      |
| `Type`        |       |      |
| `PackCount`   |       |      |
| `key`         |       |      |
