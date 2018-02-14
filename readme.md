---------------------------*********************-----------------------

-  composer install

-  php artisan vendor:publish

-  php artisan migrate

-  php artisan serve



----- Register    (POST) ---------

http://localhost:8000/api/v1/register 

params=

{

    firstname = "gold",

    lastname = 'Bright',

    email = 'gold@bright.com',

    password = '123456',

    password_confirmation = '123456',

}

Notice : These 4 fields are required ones.

response = 

{

   "status": "success",

    "status_code": 200,

    "message": "Login successful!",

    "data": {

        "UID": 9,

        "status": 0,

        "api_token": 
        
        "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjksImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9hcGkvdjEvcmVnaXN0ZXIiLCJpYXQiOjE1MTg1NDE0OTgsImV4cCI6MTUxODU0NTA5OCwibmJmIjoxNTE4NTQxNDk4LCJqdGkiOiJvdWtWaXFpazd6YkZNTTlrIn0.oegf1o7X7MQigwzfCg-NyTGELWS7NYLm_LzPxsamE0M"

    }

}

Notice :

Once you register or login the api_token will be created.

You must get this api_token after successful login. It is used for further action such as `update`.

----- update    (POST)--------------

http://localhost:8000/api/v1/update 

params = 

{

    uid = 9,

    transaction_id = '123123123123123123123123123112312',

    product_id = 'product_id test',

    ...

    original_purchase_date = '2018/2/3/324234',

    ...

    api_token = 
    
    'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjksImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9hcGkvdjEvcmVnaXN0ZXIiLCJpYXQiOjE1MTg1NDE0OTgsImV4cCI6MTUxODU0NTA5OCwibmJmIjoxNTE4NTQxNDk4LCJqdGkiOiJvdWtWaXFpazd6YkZNTTlrIn0.oegf1o7X7MQigwzfCg-NyTGELWS7NYLm_LzPxsamE0M'

}

Notice : You can update purchased info with `uid` and `transaction_id`. 

response = 

{
    
    "status": "success",

    "status_code": 200,

    "message": "Updated successful!",

    "data": {

        "UID": 9,

        "transaction_id": "123123123123123123123123123112312",

        ...

        "status": 1

    }

}

------------ logout     (GET) -------------------

http://localhost:8000/api/v1/logout/{api_token}

Notice : Once logout then the api_token will be expired.

In the db the api_token field is formated as NULL.

(ex)

http://localhost:8000/api/v1/logout/eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjksImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9hcGkvdjEvcmVnaXN0ZXIiLCJpYXQiOjE1MTg1NDE0OTgsImV4cCI6MTUxODU0NTA5OCwibmJmIjoxNTE4NTQxNDk4LCJqdGkiOiJvdWtWaXFpazd6YkZNTTlrIn0.oegf1o7X7MQigwzfCg-NyTGELWS7NYLm_LzPxsamE0M

response =

{

    "status": "success",

    "status_code": 200,

    "message": "Logout successful!"

}

-------------------- login      (POST) -------------------

http://localhost:8000/api/v1/login 

params = 

{

	email = 'gold@bright.com',

	password = '123456'

}

Notice : These 2 fields are required.

response =

{

    "status": "success",

    "status_code": 200,

    "message": "Login successful!",

    "data": {

        "UID": 9,

        "status": 1
,
        "api_token":

        "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjksImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9hcGkvdjEvbG9naW4iLCJpYXQiOjE1MTg1NDcxNjUsImV4cCI6MTUxODU1MDc2NSwibmJmIjoxNTE4NTQ3MTY1LCJqdGkiOiJIQ3A4NER5VjFIeVo4dG5MIn0.BGXey_yc7QCDwz3hva6SKdHPcV6Y1HeIHqj6gbP026k"
    
    }

}

or 

{

    "status": "success",

    "status_code": 200,

    "message": "Already logged in",

    "user": {

        "UID": 9,

        "status": 1,

        "api_token":

        "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjksImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6ODAwMC9hcGkvdjEvbG9naW4iLCJpYXQiOjE1MTg1NDcxNjUsImV4cCI6MTUxODU1MDc2NSwibmJmIjoxNTE4NTQ3MTY1LCJqdGkiOiJIQ3A4NER5VjFIeVo4dG5MIn0.BGXey_yc7QCDwz3hva6SKdHPcV6Y1HeIHqj6gbP026k"

    }

}