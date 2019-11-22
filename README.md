# travelapi
# Sử dụng api filter 
- Các params truyền lên theo một cấu trúc nhất định :
  ```
  [ tên_atrribute ] : {
      "type" : [type],
      "value" : [value]
  }
  ```
  + tên_attribute : tên thuộc tính dùng để filter
  + type nhận một trong các giá trị [ "=", "like" , "asc", "desc", "compare"] 
  + value : giá trị của thuộc tính 
 ```
 {
  "name" : {
    "type" : "like",
    "value" : "peago"
  }
 }
 ```
 kết quả filter sẽ chứa các bản ghi có trường name chứa "peago".

 - Chú ý : 
  + value truyền lên có thể là mảng.
  + Nếu type = "compare", value sẽ có cấu trúc như sau : 
  ```
  {
    "type" : "compare",
    "value" : {
      "from" : [value_from],
      "to" : [value_to]
      }
    }  
  ```
  - Các params đặc biệt sẽ không theo cấu trúc trên
    + search :
    ```
    {
      "search" : [search_string]
    } 
    ```
    
    + sort :
     ``` 
     {
       "sort" : {
         "type" : enum("asc", "desc"),
         "attr" : [thuộc_tính_sắp_xếp]
       }
     } 
     ```
    + paging :
    ``` 
    {
      "paging" : {
          "itemsPerPage" : [số_item_1_trang],
          "page" : [trang]
      }
    } 
    ```
- Ví dụ một params gọi api  :
 ``` 
 {
    "sort": {
	    "type" : "asc",
	    "attr" : "id"
	    },
    "created_at" : {
	    "type" : "compare",
	    "value" : {
		      "from" : "2019-01-01",
		      "to" : "2019-12-31"
	     }
	    },
    "email" : {
	      "type" : "like",
	      "value" : "example@mail.com"
	    },
    "username" : {
	      "type" : "like",
	      "value" : "peago"
	     },
    "age" : {
        "type" : "=",
        "value" : 20
       },
    "gender": {
	      "type" : "",
	      "value" : ["male", "female"]
       },
    "search": "something",
    "paging" : {
	      "itemsPerPage" : 5,
	      "page" : 1
       }
 }
```

 
