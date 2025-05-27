Pass Throug Initiate


``` bash
curl --location 'https://middleware.dev-sheba.xyz/addmapi/v1/add-money/card/initiate' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzZXJ2aWNlTmFtZSI6ImFkZF9tb25leSIsImlhdCI6MTczMDE0MDQ2MCwiZXhwIjoxNzMyNzMyNDYwfQ.zBbh0H3YoRorcPdGutrCFNtTCppexg_UpY9QxlOljCc' \
--header 'ServiceName: add_money' \
--header 'Content-Type: application/json' \
--data '{
    
    "passThrough":{
        "source":"8801718610610", 
        "dest":"8801620011009", 
        "amount":50,
        "serviceType":"mPay", 
        "bqrBody": { 
            "hu":"zaifa"
        }
    },
    "amount": 50.00,
    "msisdn": "8801718610610",
    "cardType": "visa", 
    "cardNumber": 4000000000002503, 
    "cardHolderName": "AL Zami Arafat",
    "cavv": "123",
    "expiry": "05/35",
    "description": null
}'
```

body with Helpfull comment

```json
{
    // "linkedAccountId":201,
    "passThrough":{
        "source":"8801718610610", 
        "dest":"8801620011009", 
        "amount":50,
        "serviceType":"mPay", // mPay for normal payment, bPay for bqr payment
        "bqrBody": { // bqr payload herer. mandatory if bPay
            "hu":"zaifa"
        }
    },
    "amount": 50.00,
    "msisdn": "8801718610610",
    "cardType": "visa", 
    "cardNumber": 4000000000002503, 
    "cardHolderName": "AL Zami Arafat",
    "cavv": "123",
    "expiry": "05/35",
    "description": null
}
```

---

payment AML

```bash
curl --location 'https://middleware.dev-sheba.xyz/walletpayapi/v1/wallet-transactions/payment/aml' \
--header 'serviceName: supplier_payment_service' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzZXJ2aWNlTmFtZSI6InN1cHBsaWVyX3BheW1lbnRfc2VydmljZSIsImlhdCI6MTczODU5MDM3MywiZXhwIjoxNzQxMTgyMzczfQ.ECP8_MB-aQOHrKnajEVOCgoW15rzmTsNErSxMEDbi4g' \
--header 'Content-Type: application/json' \
--data '{
    "source": "8801718610610",
    "amount": "50",
    "dest": "8801813148110",
    "pin": "111111",
    "serviceType": "mPay" 
}'
```

body with helpful comment

```json
{
    "source": "8801718610610",
    "amount": "50",
    "dest": "8801813148110", // must for mPay.
    "pin": "111111",
    "serviceType": "mPay" // mPay for normal payment, bPay for bqr payment
}
```

---

bqr payment. 

```bash
curl --location 'https://middleware.dev-sheba.xyz/walletpayapi/v1/wallet-transactions/payment/bqr' \
--header 'serviceName: supplier_payment_service' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzZXJ2aWNlTmFtZSI6InN1cHBsaWVyX3BheW1lbnRfc2VydmljZSIsImlhdCI6MTczODU5MDM3MywiZXhwIjoxNzQxMTgyMzczfQ.ECP8_MB-aQOHrKnajEVOCgoW15rzmTsNErSxMEDbi4g' \
--header 'Content-Type: application/json' \
--data '{
  "dest_pan": 9100521246272855,
  "source_pan": 8801678242957,
  "amount": 1,
  "merchant_category": 5411,
  "point_of_initiation_method": 11,
  "dest_business_name": "NAZMUL FOL VANDER",
  "dest_address": "Rangpur",
  "currency_code": "050",
  "pin": 119747,
  "emvData": {
    "emvqr": {
      "payloadFormatIndicator": {
        "tag": "00",
        "lenght": "02",
        "value": "01"
      },
      "pointOfInitiationMethod": {
        "tag": "01",
        "lenght": "02",
        "value": "11"
      },
      "merchantAccountInformation": {
        "26": {
          "tag": "26",
          "length": "46",
          "value": {
            "globallyUniqueIdentifier": {
              "tag": "00",
              "lenght": "08",
              "value": "TallyPay"
            },
            "paymentNetworkSpecific": [
              {
                "tag": "01",
                "lenght": "02",
                "value": "03"
              },
              {
                "tag": "02",
                "lenght": "04",
                "value": "1005"
              },
              {
                "tag": "03",
                "lenght": "16",
                "value": "9100521246272855"
              }
            ]
          }
        }
      },
      "merchantCategoryCode": {
        "tag": "52",
        "lenght": "04",
        "value": "5411"
      },
      "transactionCurrency": {
        "tag": "53",
        "lenght": "03",
        "value": "050"
      },
      "transactionAmount": null,
      "tipOrConvenienceIndicator": null,
      "valueOfConvenienceFeeFixed": null,
      "valueOfConvenienceFeePercentage": null,
      "countryCode": {
        "tag": "58",
        "lenght": "02",
        "value": "BD"
      },
      "merchantName": {
        "tag": "59",
        "lenght": "17",
        "value": "NAZMUL FOL VANDER"
      },
      "merchantCity": {
        "tag": "60",
        "lenght": "07",
        "value": "Rangpur"
      },
      "postalCode": null,
      "additionalDataFieldTemplate": {
        "tag": "62",
        "length": "39",
        "value": {
          "billNumber": null,
          "mobileNumber": null,
          "storeLabel": {
            "tag": "03",
            "lenght": "12",
            "value": "ST1246272855"
          },
          "loyaltyNumber": null,
          "referenceLabel": null,
          "customerLabel": null,
          "terminalLabel": {
            "tag": "07",
            "lenght": "08",
            "value": "00000001"
          },
          "purposeTransaction": {
            "tag": "08",
            "lenght": "07",
            "value": "PAYMENT"
          },
          "additionalConsumerDataRequest": null,
          "merchantTaxID": null,
          "merchantChannel": null,
          "rfuForEMVCo": [],
          "paymentSystemSpecific": []
        }
      },
      "crc": {
        "tag": "63",
        "lenght": "04",
        "value": "1346"
      },
      "merchantInformationLanguageTemplate": null,
      "rfuForEMVCo": [],
      "unreservedTemplates": {}
    },
    "error": null
  },
  "loyaltyNumber": "",
  "referenceLabel": "",
  "terminalLabel": "00000001",
  "purposeTransaction": "PAYMENT"
}
'
```

