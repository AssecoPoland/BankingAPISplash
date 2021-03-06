## Welcome to the Banking API

Our API allows easy and secure access to bank accounts, customer data, many payment methods, and much more.

Our APIs are RESTful. We use JSON format and OAuth authorization based on JSON Web Token.

This API is a sandbox version, and its purpose is to make developers familiar with the upcoming API production releases. Moreover, it allows the developers to experiment and build applications, which can use the API, before its official release. See sandbox for more information regarding the sandbox and what it is.

The purpose of this documentation is to give an overview of all the APIs, which are included in API sandbox. There is separate documentation for each API, which includes the full API reference of the particular API and any specific information which is not presented in this overview.

### Table of content

- [Getting Started](#getting-started)
  * [Test data](#test-data)
  * [Security issue](#security-issue)
- [Business domain](#business-domain)
  * [/user](#user)
  * [/account](#account)
  * [/payments](#payments)
  * [/transaction](#transaction)
  * [/credit](#credit)
  * [/deposit](#deposit)
  * [/card](#card)
  * [/card_transaction](#card_transaction)
- [Tools](#tools)
- [Sandbox](#sandbox)

### Getting Started

To start working with our API, you need information about:
- apiAddress - address of Your sanbox
```
https://cbp-api.asseco.pl/retail-banking-swagger/index.html
```
- jwtToken - authorization token which is provided by our organization
- customerId - internal customer's identificator in the bank
- accessProfileId - internal customer's profile identificator in the bank

#### Test data:

***Customer 1***


- jwtToken

``` 
Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNlIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDU5Iiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMjY3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.BDG474G1M7FDdGRxOAVxXYhplnoWgr0YSn6WEVOhg6Y 
```

- customerId

```
328059
```

- accessProfileId

```
2267
```  

***Customer 2***


- jwtToken

``` 
Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg
```
- customerId

```
328072
``` 

- accessProfileId

```
2307
```  


Below is a simple curl GET request to our API:
Before use, please fill required parameters: jwtToken, apiAddress, customerId.

``` 
curl -k -X GET --header "Accept: application/json" --header "Authorization: jwtToken" "https://apiAddress/api/user/get/user_personal_details.json?customerId=customerId"
```

### Security issue

Production security flow is based on the OAuth2 flow and it's described below:

     ----------------------Production--------------------------
     +--------+                               +---------------+
     |        |--(A)- Authorization Request ->|   Resource    |
     |        |                               |     Owner     |
     |        |<-(B)-- Authorization Grant ---|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(C)-- Authorization Grant -->| Authorization |
     | Client |                               |     Server    |
     |        |<-(D)----- Access Token -------|               |
     |        |                               +---------------+
     |        |
     ------------------------Sandbox---------------------------
     |        |                               +---------------+
     |        |--(E)----- Access Token ------>|    Resource   |
     |        |                               |     Server    |
     |        |<-(F)--- Protected Resource ---|               |
     +--------+                               +---------------+

In the sandbox, we provide for you ready to use JWT token, which will not expire.

### Business domain

#### /user
This resource describes personal information about bank's customers. The user is in relation with following financial resources.

***Endpoint URL***
```
/api/user/get/user_personal_details.json
```

***Curl***
```
curl -k -X GET --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/user/get/user_personal_details.json?customerId=328072'
```

***Response Body***
```json
{
  "customerId": "328072",
  "firstName": "JAN",
  "lastName": "KOWAL",
  "personalIdentificationNumber": "55010842827",
  "emailAddress": null,
  "phoneNumber": "48507507507",
  "documentType": null,
  "documentNumber": "DD5609234",
  "domicileStreetAddress": "ul. NOWA 11/11",
  "domicileApartmentNo": null,
  "domicilePostalCode": "34-456",
  "domicileCity": "RZESZÓW",
  "domicileCountry": null,
  "correspondenceStreetAddress": null,
  "correspondencePostalCode": null,
  "correspondenceCity": null,
  "correspondenceCountry": null,
  "fullName": "KOWAL JAN|ul. NOWA 11/11|34-456 RZESZÓW",
  "employe": false,
  "type": "I"
}
```

#### /account
This resource describe a basic banking product - account. It's the financial registry closely related to a bank customer. Main property of this resource is an account's balance.

***Endpoint URL***
```
/api/account
```

***Curl***
```
curl -k -X GET --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNlIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDU5Iiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMjY3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.BDG474G1M7FDdGRxOAVxXYhplnoWgr0YSn6WEVOhg6Y' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/account?customerId=328059&accessProfileId=2267&pageNumber=1&pageSize=10'
```
***Response body***
```json
{
  "totalElements": 2, 
  "pageNumber": 1,
  "pageSize": 10,
  "totalPages": 1,
  "sortOrder": null,
  "sortDirection": null,
  "content": [
    {
      "accountId": "750879",
      "productType": "ACCOUNT",
      "accountName": "Rachunek oszczędnościowo-rozliczeniowy osób prywatnych",
      "accountNo": "41161011332016015000200001",
      "accessibleAssets": 49999.99,
      "currentBalance": 50000,
      "allowedLimit": 0,
      "description": null,
      "openDate": 1490997600000,
      "blockAssets": null,
      "arrearAmount": 0,
      "ownerName": "NOWAK KONRAD",
      "accountInterest": 0.5,
      "creditInterest": 44,
      "currency": "PLN",
      "settlementPeriodDtType": null,
      "settlementPeriodCtType": null,
      "settlementPeriodDt": null,
      "settlementPeriodCt": null,
      "nextCapitalizationDtDate": null,
      "nextCapitalizationCtDate": null,
      "lastTransactionBookingDate": 1490997600000,
      "accountStatementDetails": null,
      "ownersList": [
        {
          "customerId": "328059",
          "relationType": "OWNER",
          "name": "NOWAK KONRAD",
          "addressStreetPrefix": "ul.",
          "addressStreet": "POKĄTNA",
          "houseNo": "1",
          "apartmentNo": "11",
          "postCode": "47-200",
          "town": "PRZEMYŚL",
          "country": "POLAND",
          "fullName": null,
          "originalOwner": false
        }
      ],
      "category": null,
      "subProduct": null,
      "relation": null,
      "statementDistributionType": "other",
      "modulo": "1500020",
      "commissionPackage": null,
      "unitId": 946,
      "spareAmount": null,
      "ownerEntityCode": 282,
      "accountVatId": null,
      "accountType": "RB",
      "customName": null
    },
    {
      "accountId": "750881",
      "productType": "ACCOUNT",
      "accountName": "Rachunek bieżący walutowy dla firm.",
      "accountNo": "14161011332016015000200002",
      "accessibleAssets": 50000,
      "currentBalance": 50000,
      "allowedLimit": 0,
      "description": null,
      "openDate": 1490997600000,
      "blockAssets": null,
      "arrearAmount": 0,
      "ownerName": "NOWAK KONRAD",
      "accountInterest": 0.1,
      "creditInterest": 0,
      "currency": "EUR",
      "settlementPeriodDtType": null,
      "settlementPeriodCtType": null,
      "settlementPeriodDt": null,
      "settlementPeriodCt": null,
      "nextCapitalizationDtDate": null,
      "nextCapitalizationCtDate": null,
      "lastTransactionBookingDate": 1490997600000,
      "accountStatementDetails": null,
      "ownersList": [
        {
          "customerId": "328059",
          "relationType": "OWNER",
          "name": "NOWAK KONRAD",
          "addressStreetPrefix": "ul.",
          "addressStreet": "POKĄTNA",
          "houseNo": "1",
          "apartmentNo": "11",
          "postCode": "47-200",
          "town": "PRZEMYŚL",
          "country": "POLAND",
          "fullName": null,
          "originalOwner": false
        }
      ],
      "category": null,
      "subProduct": null,
      "relation": null,
      "statementDistributionType": "other",
      "modulo": "1500020",
      "commissionPackage": null,
      "unitId": 946,
      "spareAmount": null,
      "ownerEntityCode": 282,
      "accountVatId": null,
      "accountType": "RB",
      "customName": null
    }
  ],
  "numberOfElements": 2,
  "firstPage": true,
  "lastPage": true
}
```

#### /payments
This resource is created after the bank's customer decides to make some transaction on his/her account (e.g. money transfer to internal or external account). Every payment has at least its amount, currency and status. Status decides about the payment's state. Not every payment has effect on account's balance, because of possibility of payment rejection by the system or user cancellation.

***Endpoint URL***
```
/api/payments/create_domestic_transfer
```

***Curl***
```
curl -k -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg' -d '{ \ 
   "amount": 3, \ 
   "currency": "PLN", \ 
   "description": [ \ 
     "Opłata za prąd" \ 
   ], \ 
   "intent": "realize", \ 
   "realizationDate": "2018-09-17T10:52:43.589Z", \ 
   "recipientAccountNo": "80249000059984455911456320", \ 
   "recipientAddress": [ \ 
     "ul.Dworcowa, Poznań" \ 
   ], \ 
   "recipientName": [ \ 
     "Aleksander Sas" \ 
   ], \ 
   "remitterAccountId": "750888" \ 
 }' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/payments/create_domestic_transfer'
```

***Response body***
```json
{
  "content": "3697364",
  "_links": {}
}
```

***Response body for wrong request (invalid recipientAccountNo parameter)***
```json
{
  "type": "warn",
  "subType": "validation",
  "text": null,
  "errors": [
    {
      "codes": [
        "NRB.payments.recipientAccountNo",
        "NRB.recipientAccountNo",
        "NRB"
      ],
      "arguments": [
        {
          "codes": [
            "payments.recipientAccountNo",
            "recipientAccountNo"
          ],
          "arguments": null,
          "defaultMessage": "recipientAccountNo",
          "code": "recipientAccountNo"
        }
      ],
      "defaultMessage": "validate.invalid_account_number",
      "objectName": "payments",
      "field": "recipientAccountNo",
      "rejectedValue": "wrongAccountNumber",
      "bindingFailure": false,
      "code": "NRB"
    }
  ],
  "errorIdentifier": null
}
```

***Validation errors***

Key | Description
:-----|:-----
error.swift_code.is.blank | SWIFT code is empty
error.exceeds.available.funds.for.agreement | The amount exceeds the available funds
error.lack.of.access.in.active.mode | No permission for debiting the account
error.account.of.restricted.access.product | No permission for debiting the account - restricted access to contract
error.recipient.account.is.the.same.as.the.sender | Debited account is the same as beneficiary account
error.recipient.account.number.is.blank | Benificiary account is empty
error.recipient.name.is.blank | Beneficiary name is empty
error.recipient.address.is.blank | Beneficiary address is empty
error.invalid.currency.for.insurance.transfer | Invalid operation type for foreign account
error.invalid.currency.for.standard.transfer | Invalid operation type for foreign account
error.invalid.remmitter.account.for.sepa.transfer | Account to be debited should be in PLN or EUR
error.invalid.currency.for.sepa.transfer | Incorrect currency for SEPA transfer.
error.express_elixir.invalid_date | Incorrect date
error.express_elixir.bank_not_participate_in_system | Benificiary's bank is not Express Elixir participant
error.express_elixir.service_unavailable_for_beneficiary_bank | Beneficiary's bank is unavailable in Express Elixir at the moment
error.remitter.account.is.not.with.polish.currency | Debited account is not in polish currency
error.description.title.is.too.long | Transfer title is too long
error.remitter.account.is.vat.account | Sender's account cannot be VAT account
error.account.is.vat.account | Account is VAT account
error.account.has.no.vat.account | Account is the same as tax office's
validate_recipient_account.is.tax.office.account | Account is the same as tax office's
error.change.clearing.system | Invalid type of payment, automatic change of payment type
error.invalid_account_iban | Incorrect account number



#### /transaction
This resource is created after the customer made some payments and these payments were booked in Core Banking System (in other words - payment was executed and this operation had influence on account's balance).
Particular transaction is connected with payment, from which it was created.

***Endpoint URL***
```
/api/transaction
```

***Curl***
```
curl -k -X GET --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/transaction?accountId=750888&dateFrom=2018-09-17T10%3A00%3A43.589Z&dateTo=2018-09-17T11%3A52%3A43.589Z&pageNumber=1&pageSize=10'
```

***Response body***
```json
{
  "totalElements": 1,
  "pageNumber": 1,
  "pageSize": 10,
  "totalPages": 1,
  "sortOrder": null,
  "sortDirection": null,
  "content": [
    {
      "id": 3697364,
      "referenceNumber": null,
      "accountId": 750888,
      "accountNo": "87161011332016015000250001",
      "transactionDate": 1537183642000,
      "bookingDate": 1537183642000,
      "transactionTypeDesc": null,
      "transactionType": "DOMESTIC_TRANSFER",
      "transactionSubType": "1",
      "balanceAfterOperation": 49997,
      "oppositeAccountNo": "80249000059984455911456320",
      "remitterBank": null,
      "remitter": [
        "JAN KOWAL"
      ],
      "beneficiaryBank": null,
      "beneficiary": [
        "Aleksander Sas"
      ],
      "description": [
        "Opłata za prąd"
      ],
      "title": null,
      "amountInAccountCurrency": null,
      "accountCurrency": "PLN",
      "amount": 3,
      "currency": "PLN",
      "side": "DEBIT",
      "remitterSwift": null,
      "beneficiarySwift": null,
      "foreignBank": null,
      "transactionUsDetails": null,
      "transactionZusDetails": null,
      "decreeType": null
    }
  ],
  "numberOfElements": 1,
  "firstPage": true,
  "lastPage": true
}
```

#### /credit
This resource reflects customer's financial liabilities towards the bank.

***Endpoint URL***
```
/api/credit
```

***Curl***
```
curl -k -X GET --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/credit?customerId=328072&pageNumber=1&pageSize=10'
```
***Response body***
```json
{
  "totalElements": 1,
  "pageNumber": 1,
  "pageSize": 10,
  "totalPages": 1,
  "sortOrder": null,
  "sortDirection": null,
  "content": [
    {
      "creditId": "750893",
      "accountNo": "41161011331016015000250001",
      "currency": "PLN",
      "creditAmount": 30000,
      "creditName": "Kredyt mieszkaniowy",
      "maturedCapitalAmount": 0,
      "unmaturedCapitalAmount": 30000,
      "nextInstallmentAmount": 1014.2,
      "nextInstallmentDate": 1537740000000,
      "overpaymentAmount": 0,
      "overpaymentCurrency": "PLN",
      "outstandingLiabilitiesAmount": 0,
      "outstandingLiabilitiesCurrency": "PLN",
      "interestRate": 11,
      "openDate": 1490997600000,
      "closeDate": 1584918000000,
      "ownersList": [
        {
          "customerId": "328072",
          "relationType": "OWNER",
          "name": "KOWAL JAN",
          "addressStreetPrefix": null,
          "addressStreet": null,
          "houseNo": null,
          "apartmentNo": null,
          "postCode": null,
          "town": null,
          "country": null,
          "fullName": null,
          "originalOwner": false
        }
      ],
      "lastTransactionBookingDate": null
    }
  ],
  "numberOfElements": 1,
  "firstPage": true,
  "lastPage": true
}
```

#### /deposit
This resource is connected with customers savings.

***Endpoint URL***
```
/api/deposit
```

***Curl***
```
curl -k -X GET --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/deposit?customerId=328072&pageNumber=1&pageSize=10'
```
***Response body***
```json
{
  "totalElements": 1,
  "pageNumber": 1,
  "pageSize": 10,
  "totalPages": 1,
  "sortOrder": null,
  "sortDirection": null,
  "content": [
    {
      "depositId": "750892",
      "depositName": "Depozyt \"Pewniak\"",
      "description": null,
      "accountNo": "36161011333016015000250001",
      "currency": "PLN",
      "depositBalance": 555,
      "nextCapitalizationDate": 1506895200000,
      "maturityDate": 1506895200000,
      "openingAccountNo": "87161011332016015000250001",
      "settlementAccountNo": null,
      "settlementAccountIntNo": null,
      "renewalOptionType": "RENEWAL_WITH_INTEREST",
      "depositPeriodType": "MONTH",
      "period": 6,
      "interest": 0,
      "interestRateType": "FIXED",
      "openDate": 1490997600000,
      "productType": "DEPOSIT",
      "isSurcharge": false,
      "nextSurchargeDate": null,
      "nextSurchargeAmount": 0,
      "lastSurchargeAmount": null,
      "ownersList": [
        {
          "customerId": "328072",
          "relationType": "OWNER",
          "name": "KOWAL JAN",
          "addressStreetPrefix": null,
          "addressStreet": null,
          "houseNo": null,
          "apartmentNo": null,
          "postCode": null,
          "town": null,
          "country": null,
          "fullName": null,
          "originalOwner": false
        }
      ],
      "contractStatus": "ACTIVE",
      "unfinishedDisposition": false,
      "typeCapableToBreak": true,
      "lastTransactionBookingDate": 1490997600000,
      "profitAmount": null,
      "commentary": null,
      "dispositionStatus": null,
      "settlementAccountId": "8442",
      "surcharge": false
    }
  ],
  "numberOfElements": 1,
  "firstPage": true,
  "lastPage": true
}
```

#### /card
This resource reflects a customer's payment cards (credit/debit). Every card is connected to customer's account.

***Endpoint URL***
```
/api/card
```

***Curl***
```
curl -k -X GET --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/card?customerId=328072&accessProfileId=2307&cardStatus=ALL&pageNumber=1&pageSize=10'
```
***Response body***
```json
{
  "totalElements": 2,
  "pageNumber": 1,
  "pageSize": 10,
  "totalPages": 1,
  "sortOrder": null,
  "sortDirection": null,
  "content": [
    {
      "id": "2443",
      "name": "KREDYT",
      "cardNo": "22xx xxxx xxxx 6739",
      "availableFunds": 5000,
      "accountId": "750895",
      "accountNo": "14161011331016015000250002",
      "cardOwnerName": "JAN KOWAL",
      "cardOwnerLastName": null,
      "status": "ACTIVE",
      "active": true,
      "cardType": "CREDIT",
      "cardSubType": "MAIN",
      "currency": "PLN",
      "blockedFunds": 0,
      "dateExpirationEnd": 1607727600000,
      "settlmntDate": 1492725600000,
      "limitLeft": null,
      "cardDetails": {
        "dateExpirationStart": null,
        "dailyTrxLimit": null,
        "dailyCashLimit": null,
        "dailyTrxLimitCount": 0,
        "dailyCashLimitCount": 0,
        "maxDailyTrxLimit": null,
        "maxDailyCashLimit": null,
        "maxDailyTrxLimitCount": 0,
        "maxDailyCashLimitCount": 0,
        "cardLimits": [
          {
            "code": "SBI_LIMIT",
            "description": "Opis typu",
            "value": 12,
            "valueMax": 300
          },
          {
            "code": "SBI5_LIMIT",
            "description": "Opis typu",
            "value": 13,
            "valueMax": 300
          },
          {
            "code": "SBI4_LIMIT",
            "description": "Opis typu",
            "value": 12,
            "valueMax": 300
          },
          {
            "code": "SBI1_LIMIT",
            "description": "Opis typu",
            "value": 12,
            "valueMax": 300
          }
        ]
      },
      "lastOperationDate": null,
      "balance": null,
      "holders": null,
      "owner": null,
      "customName": null,
      "embossedName": null
    },
    {
      "id": "2463",
      "name": "KREDYT",
      "cardNo": "11xx xxxx xxxx 6739",
      "availableFunds": 50000,
      "accountId": "750888",
      "accountNo": "87161011332016015000250001",
      "cardOwnerName": "JAN KOWAL",
      "cardOwnerLastName": null,
      "status": "ACTIVE",
      "active": true,
      "cardType": "DEBIT",
      "cardSubType": "MAIN",
      "currency": "PLN",
      "blockedFunds": 0,
      "dateExpirationEnd": 1607727600000,
      "settlmntDate": null,
      "limitLeft": null,
      "cardDetails": {
        "dateExpirationStart": null,
        "dailyTrxLimit": null,
        "dailyCashLimit": null,
        "dailyTrxLimitCount": 0,
        "dailyCashLimitCount": 0,
        "maxDailyTrxLimit": null,
        "maxDailyCashLimit": null,
        "maxDailyTrxLimitCount": 0,
        "maxDailyCashLimitCount": 0,
        "cardLimits": [
          {
            "code": "SBI_LIMIT",
            "description": "Opis typu",
            "value": 12,
            "valueMax": 300
          }
        ]
      },
      "lastOperationDate": null,
      "balance": null,
      "holders": null,
      "owner": null,
      "customName": null,
      "embossedName": null
    }
  ],
  "numberOfElements": 2,
  "firstPage": true,
  "lastPage": true
}
```

#### /card_transaction
This resource contains all information about financial operations within the card (e.g. withdrawing cash from an ATM, internet payments or payments in traditional shops).

***Endpoint URL***
```
/api/card_transaction
```

***Curl***
```
curl -k -X GET --header 'Accept: application/json' --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOlsicmViLWN1c3RvbWVyLXNlcnZpY2UiXSwidXNlcl9uYW1lIjoiTUIxQk1PNVIiLCJpZGVudGl0eSI6eyJvcmdfdW5pdCI6Im91PTk0NixvPVNHQi1CQU5LLGRjPUFDUCxkYz11ZmUsZGM9Y29tIiwicGVyc29uX2lkIjoiMzI4MDcyIiwicm9sZSI6IkNVU1RPTUVSIiwiYWNjZXNzX3Byb2ZpbGVfaWQiOiIyMzA3In0sInNjb3BlIjpbIndyaXRlIiwicmVhZCJdLCJpc3MiOiJpc3N1ZXIiLCJqdGkiOiJlYmY0ZGZmYS00ZWU2LTQ4NGUtODdiMy1hYzc5MDk3ZWRmZjUiLCJjbGllbnRfaWQiOiJyZWJSZXRhaWwiLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXX0.cQRnONmhv4WR8p3tTSjXZXYo45Xt46R_OptL-2Nj2Mg' 'https://cbp-api.asseco.pl/retail-banking-swagger/api/card_transaction?customerId=328072&accessProfileId=2307&cardId=2463&dateFrom=2017-04-01T00%3A00%3A10.589Z&dateTo=2018-09-12T00%3A00%3A10.589Z&pageNumber=1&pageSize=10'
```

***Response body***
```json
{
  "totalElements": 8,
  "pageNumber": 1,
  "pageSize": 10,
  "totalPages": 1,
  "sortOrder": null,
  "sortDirection": null,
  "content": [
    {
      "id": "3697155",
      "description": [
        "Wpłata"
      ],
      "amount": 50000,
      "accountAmount": 50000,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1490997600000,
      "transactionDate": 1490997600000,
      "transactionType": null,
      "transactionTypeDesc": "Wpłata na rachunek",
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": null,
      "remitterSwift": null,
      "remitter": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "side": "CREDIT",
      "balanceAfterOperation": 50000
    },
    {
      "id": "3697157",
      "description": [
        "Test"
      ],
      "amount": -7,
      "accountAmount": -7,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1490997600000,
      "transactionDate": 1490997600000,
      "transactionType": null,
      "transactionTypeDesc": "Przelew wychodzący zewnętrzny",
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": null,
      "remitterSwift": null,
      "remitter": [
        "JAN KOWAL",
        "",
        "ul. NOWA 11/11 ",
        "34-456 RZESZÓW"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "Test"
      ],
      "side": "DEBIT",
      "balanceAfterOperation": 49993
    },
    {
      "id": "3697158",
      "description": [
        "Opłaty i prowizje - Przelewy Eliksi",
        "r"
      ],
      "amount": -0.5,
      "accountAmount": -0.5,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1490997600000,
      "transactionDate": 1490997600000,
      "transactionType": null,
      "transactionTypeDesc": "Pobranie opłaty",
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": null,
      "remitterSwift": null,
      "remitter": [
        "KOWAL JAN ul. NOWA 11/11 34-456 RZESZÓW"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "SGB-Bank S.A."
      ],
      "side": "DEBIT",
      "balanceAfterOperation": 49992.5
    },
    {
      "id": "3697159",
      "description": [
        "Lokata nr DS\\17000092",
        "- założenie"
      ],
      "amount": -555,
      "accountAmount": -555,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1490997600000,
      "transactionDate": 1490997600000,
      "transactionType": null,
      "transactionTypeDesc": "Przelew wychodzący wewnętrzny",
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": null,
      "remitterSwift": null,
      "remitter": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "side": "DEBIT",
      "balanceAfterOperation": 49437.5
    },
    {
      "id": "3697160",
      "description": [
        "Uruchomienie pożyczkinr KHM\\1700014"
      ],
      "amount": 30000,
      "accountAmount": 30000,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1490997600000,
      "transactionDate": 1490997600000,
      "transactionType": null,
      "transactionTypeDesc": "Przelew przychodzący wewnętrzny",
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": "SGB-BANK Oddział - Finansowe Centrum Biznesu w Poznaniu",
      "remitterSwift": null,
      "remitter": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "side": "CREDIT",
      "balanceAfterOperation": 79437.5
    },
    {
      "id": "3697163",
      "description": [
        "Wypłata własna"
      ],
      "amount": -19437.5,
      "accountAmount": -19437.5,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1490997600000,
      "transactionDate": 1490997600000,
      "transactionType": null,
      "transactionTypeDesc": "Wypłata z rachunku",
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": null,
      "remitterSwift": null,
      "remitter": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "side": "DEBIT",
      "balanceAfterOperation": 60000
    },
    {
      "id": "3697164",
      "description": [
        "Wypłata własna"
      ],
      "amount": -10000,
      "accountAmount": -10000,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1490997600000,
      "transactionDate": 1490997600000,
      "transactionType": null,
      "transactionTypeDesc": "Wypłata z rachunku",
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": null,
      "remitterSwift": null,
      "remitter": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "KOWAL JAN",
        "ul. NOWA 11/11",
        "34-456 RZESZÓW"
      ],
      "side": "DEBIT",
      "balanceAfterOperation": 50000
    },
    {
      "id": "3697344",
      "description": null,
      "amount": -0.01,
      "accountAmount": null,
      "settlementAmount": null,
      "currency": "PLN",
      "accountCurrency": "PLN",
      "settlementCurrency": null,
      "exchange": null,
      "accountingDate": 1536665547000,
      "transactionDate": 1536665547000,
      "transactionType": null,
      "transactionTypeDesc": null,
      "accountNo": "87161011332016015000250001",
      "oppositeAccountNo": null,
      "remitterBank": null,
      "remitterSwift": null,
      "remitter": [
        "JAN KOWAL"
      ],
      "beneficiaryBank": null,
      "beneficiarySwift": null,
      "beneficiary": [
        "RecipientName"
      ],
      "side": "DEBIT",
      "balanceAfterOperation": 49999.99
    }
  ],
  "numberOfElements": 8,
  "firstPage": true,
  "lastPage": true
}
```

### Tools

To integrate with our RESTful API you can use your favourite tool. We suggest:  
[PostMan](https://www.getpostman.com)  
[SoapUI](https://www.soapui.org) or simply  
[Curl](https://curl.haxx.se)

### Sandbox

[Try API](https://cbp-api.asseco.pl/retail-banking-swagger/index.html)
