# Filter & Pagination in Django

- Filter your result-set
- Paginate your result-set as per object you want in your response
- It's a open source service. 
- Easy to implement
- Fastest execution & High performance

---
## Install with pip
```
pip install filter-and-pagination
```

---
## How to implement
1) install package by `pip install filter-and-pagination`
2) import FilterPagination by `from filter_and_pagination import FilterPagination` in view.py
3) in your function writte code as bellow standards...
```
queryset = FilterPagination.filter_and_pagination(request, Customer)
serialize_data = CustomerSerializer(queryset['queryset'], many=True).data
resultset = {'dataset': serialize_data, 'pagination': queryset['pagination']}
```
 - in this code `Customer` is Django model &
 - `CustomerSerializer` is a DRF Serializer class

4) in the resultset it contains dataset & pagination data, In this format (API Response) link: https://github.com/ashish1997it/filter-pagination-dj#demo
5) For the API request follow PostMan collection link: https://github.com/ashish1997it/filter-pagination-dj#postman in the header section it will take a parameter & request you customize as per your requirement


---
## Demo


### Example 1:
 **Request:**
 - URL: http://127.0.0.1:8000/customers/api/v1/
 - Method: GET

**Response:**
```
{
    "status_code": 200,
    "status": "success",
    "message": [
        "Customer data retrieved successfully."
    ],
    "data": {
        "dataset": [
            {
                "id": 190,
                "name": "Kimberly",
                "full_name": "Kimberly Hernandez",
                "email": "gonzalezjustin@yahoo.com",
                "contact_no_dail_code": "97",
                "contact_no": "9881093638",
                "dob": "2005-06-08",
                "gender": 0,
                "address": "15750 John Circle\nPort Richardmouth, OK 26450",
                "extra": {},
                "created_at": "2020-09-05T06:31:33.187520Z",
                "updated_at": "2020-09-05T06:31:33.187525Z"
            },
            {
                "id": 189,
                "name": "Robert",
                "full_name": "Robert Gilbert",
                "email": "smeyer@miller-adams.com",
                "contact_no_dail_code": "145",
                "contact_no": "9885968723",
                "dob": "1904-11-04",
                "gender": 0,
                "address": "3113 Adam Port Suite 601\nMelissaview, IA 82893",
                "extra": {},
                "created_at": "2020-09-05T06:31:33.187491Z",
                "updated_at": "2020-09-05T06:31:33.187497Z"
            },
            {
                "id": 188,
                "name": "John",
                "full_name": "John Cunningham",
                "email": "joanne99@gmail.com",
                "contact_no_dail_code": "101",
                "contact_no": "9847393498",
                "dob": "2018-12-06",
                "gender": 0,
                "address": "169 Holmes Knoll Suite 326\nSouth Cole, MT 47763",
                "extra": {},
                "created_at": "2020-09-05T06:31:33.187458Z",
                "updated_at": "2020-09-05T06:31:33.187463Z"
            },
            ...(16 more recored)...
            {
                "id": 171,
                "name": "Robert",
                "full_name": "Robert Willis",
                "email": "laurie53@adams.com",
                "contact_no_dail_code": "202",
                "contact_no": "9814939456",
                "dob": "1953-04-30",
                "gender": 0,
                "address": "515 Kristina Oval\nLoganfurt, NE 57447",
                "extra": {},
                "created_at": "2020-09-05T06:31:19.465884Z",
                "updated_at": "2020-09-05T06:31:19.465903Z"
            }
        ],
        "pagination": {
            "per_page": 20,
            "current_page": 1,
            "total_count": 120,
            "total_pages": 6
        }
    }
}
```


### Example 2:
 **Request:**
 - URL: http://127.0.0.1:8000/customers/api/v1/?name=jasmin
 - Method: GET

**Response:**
```
{
    "status_code": 200,
    "status": "success",
    "message": [
        "Customer data retrieved successfully."
    ],
    "data": {
        "dataset": [
            {
                "id": 166,
                "name": "Jasmin",
                "full_name": "Jasmin Perry",
                "email": "nicolemathews@smith-anderson.net",
                "contact_no_dail_code": "186",
                "contact_no": "9831999092",
                "dob": "1936-07-27",
                "gender": 1,
                "address": "466 Zuniga Trail Suite 955\nLake Brandonside, AL 22894",
                "extra": {},
                "created_at": "2020-01-11T10:09:24.780734Z",
                "updated_at": "2020-01-11T10:09:24.780745Z"
            }
        ],
        "pagination": {
            "per_page": 20,
            "current_page": 1,
            "total_count": 1,
            "total_pages": 1
        }
    }
}
```


### Example 3:
 **Request:**
 - URL: http://127.0.0.1:8000/customers/api/v1/?per_page=50&page_no=2
 - Method: GET

**Response:**
```
{
    "status_code": 200,
    "status": "success",
    "message": [
        "Customer data retrieved successfully."
    ],
    "data": {
        "dataset": [
            {
                "id": 140,
                "name": "Brittney",
                "full_name": "Brittney Cole",
                "email": "connor46@hotmail.com",
                "contact_no_dail_code": "176",
                "contact_no": "9847701037",
                "dob": "2013-12-31",
                "gender": 1,
                "address": "691 Kristie Union Apt. 084\nSouth Jasonmouth, CO 80346",
                "extra": {},
                "created_at": "2020-01-11T09:34:38.136662Z",
                "updated_at": "2020-01-11T09:34:38.136667Z"
            },
            {
                "id": 139,
                "name": "James",
                "full_name": "James Douglas",
                "email": "klewis@walker.com",
                "contact_no_dail_code": "104",
                "contact_no": "9827625928",
                "dob": "1904-12-10",
                "gender": 1,
                "address": "9452 Andrew Fall\nNorth Lesliestad, AZ 17310",
                "extra": {},
                "created_at": "2020-01-11T09:34:38.136632Z",
                "updated_at": "2020-01-11T09:34:38.136637Z"
            },
            {
                "id": 138,
                "name": "Laura",
                "full_name": "Laura Miller",
                "email": "melinda04@bass-edwards.com",
                "contact_no_dail_code": "197",
                "contact_no": "9806070760",
                "dob": "1905-11-23",
                "gender": 1,
                "address": "20895 John Glens Suite 799\nEast Jill, TX 46598",
                "extra": {},
                "created_at": "2020-01-11T09:34:38.136602Z",
                "updated_at": "2020-01-11T09:34:38.136607Z"
            },
            ...(46 more recored)...
            {
                "id": 91,
                "name": "Steven",
                "full_name": "Steven George",
                "email": "bethany43@rogers.com",
                "contact_no_dail_code": "118",
                "contact_no": "9891505184",
                "dob": "2004-10-11",
                "gender": 1,
                "address": "339 Oliver Vista\nThomasmouth, KS 63022",
                "extra": {},
                "created_at": "2020-01-11T09:30:04.314290Z",
                "updated_at": "2020-01-11T09:30:04.314308Z"
            }
        ],
        "pagination": {
            "per_page": "50",
            "current_page": "2",
            "total_count": 120,
            "total_pages": 3
        }
    }
}
```

---
### PyPi
- Project: filter-and-pagination
- link: https://pypi.org/project/filter-and-pagination/

---
### GitHub
- Project: filter-pagination-dj
- link: https://github.com/ashish1997it/filter-pagination-dj

---
### PostMan
- Collection: filter-and-pagination-in-GH-proj
- link: https://www.getpostman.com/collections/eae09a934fbc284bc062

---
### Medium
- Article: Filter & Pagination in Django
- link: https://medium.com/@sondagarashish/filter-and-pagination-in-django-c0a61ff5f5c4

---
