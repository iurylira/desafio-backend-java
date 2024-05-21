![StoneSDK](https://cloud.githubusercontent.com/assets/2567823/11539067/6300c838-990c-11e5-9831-4f8ce691859e.png)

# Backend Challenge

The challenge is to create a REST API for the Star Wars store that will be consumed by an application (Android and iOS).
All items will be placed in a cart on the application side and passed to the API to perform an e-commerce transaction.

The candidate must **fork** this repository and after completion of development, make a **pull request** for the team to analyze.

The candidate has the freedom to carry out the challenge with the technology they find best.
You must inform which technologies were used, how to install, run and access the file [`details.txt`](https://github.com/stone-pagamentos/desafio-backend/bl

### Extra
- Use Cache
- Authentication in requests
- Use Docker
  
### POST `/starstore/product`
This method must receive a new product and insert it into a database to be consumed by the API itself.
```json
{
   "title":"Blusa do Imperio",
   "price":7990,
   "zipcode":"78993-000",
   "seller":"João da Silva",
   "thumbnailHd":"https://cdn.awsli.com.br/600x450/21/21351/produto/3853007/f66e8c63ab.jpg",
   "date":"26/11/2015"
}
```
| Field       | Type   |
|-------------|--------|
| title       | String |
| price       | int    |
| zipcode     | String |
| seller      | String |
| thumbnailHd | String |
| date        | String |


### GET `/starstore/products`
This API method must return the following JSON
```json
[
  {
    "title": "Blusa do Imperio",
    "price": 7990,
    "zipcode": "78993-000",
    "seller": "João da Silva",
    "thumbnailHd": "https://cdn.awsli.com.br/600x450/21/21351/produto/3853007/f66e8c63ab.jpg",
    "date": "26/11/2015"
  },
  {
    "title": "Blusa Han Shot First",
    "price": 7990,
    "zipcode": "13500-110",
    "seller": "Joana",
    "thumbnailHd": "https://cdn.awsli.com.br/1000x1000/21/21351/produto/7234148/55692a941d.jpg",
    "date": "26/11/2015"
  },
  {
    "title": "Sabre de luz",
    "price": 150000,
    "zipcode": "13537-000",
    "seller": "Mario Mota",
    "thumbnailHd": "http://www.obrigadopelospeixes.com/wp-content/uploads/2015/12/kalippe_lightsaber_by_jnetrocks-d4dyzpo1-1024x600.jpg",
    "date": "20/11/2015"
  }
]
```

| Field       | Type   |
|-------------|--------|
| title       | String |
| price       | int    |
| zipcode     | String |
| seller      | String |
| thumbnailHd | String |
| date        | String |


After the user adds all the desired items to the cart, they will complete the purchase.
To do this, you will need to use the `buy` method in your API.

### POST `/starstore/buy`
This method will receive purchase data, along with user data.
```json
{
   "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
   "client_name":"Luke Skywalker",
   "total_to_pay":1236,
   "credit_card":{
      "card_number":"1234123412341234",
      "value":7990,
      "cvv":789,
      "card_holder_name":"Luke Skywalker",
      "exp_date":"12/24"
   }
}

```

+ Transaction

| Field        | Type       |
|--------------|------------|
| client_id    | String     |
| client_name  | String     |
| total_to_pay | int        |
| credit_card  | CreditCard |

+ CreditCard

| Field            | Type   |
|------------------|--------|
| card_number      | String |
| card_holder_name | String |
| value            | int    |
| cvv              | int    |
| exp_date         | String |


### GET `/starstore/history`
This method must return all purchases made on the API
```json
[
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   },
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   },
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   }
]
```
| Field            | Type   |
|------------------|--------|
| card_number      | String |
| cliend_id        | String |
| value            | int    |
| date             | String |
| purchase_id      | String |

### GET `/starstore/history/{clientId}`
This method must return all purchases made on the API
```json
[
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   },
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   }
]
```




---
#### LICENSE
```
MIT License

Copyright (c) 2016 Stone Pagamentos

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
