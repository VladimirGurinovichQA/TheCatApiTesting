# TheCatApiTesting
API. Development of an API for getting Cat images

According to increased number of user requests, they do like cats and want to get their images from time to time. We're going to implement getting Cat images directly into our application.

Within this task we should develop new API with route: /images/search (https://api.thecatapi.com/images/search).

Following checks should be performed:
1. Auth Token should be valid. Otherwise: a 401 error. Authentication should be built using Header parameter "x-api-key".
2. In the case of existing parameters breed_ids or/and category_ids we should check that value/s requested exist in Breeds and Categories. Other values should be restricted with a 404 error.
3. In the case of requested mime_types we should check supported types: gif, jpg, png. Other values should be restricted with a 404 error.
4. In the case of existing parameters order=Rand, limit and page, we should restrict this request with a 400 error.
After successful check we should analyze requested parameters and provide appropriate API response including images that match to requested parameters:
- breed_ids - ids of Breeds (to get from /breeds)
- mime_types - mime types of desired images
- category_ids - ids of Categories (to get from /categories)

Also request should be structured according to requested limit of the records per page and number of page.
- limit - quantity of images to get
- page - number of page to return

Description of combining URL-params (page, limit) and other URL params:
page = 1 and limit = 25 have to get 25 cat images with requested breed_ids, mime_types and category_ids (in case of absent parameter - it's optional).
page = 3, limit = 25 have to get 25 cat images with requested breed_ids, mime_types and category_ids following previous 50 records.

By default all found records in API response should be ordered by id asc.

TASK: prepare Postman collection to test this API
-----------------------------------

VueJs. Development of UI for searching and displaying Cat Images with API integration

https://thecatapi.com/

User interface should provide following parameters:
Order - options: Random Asc (order param = empty), Desc Asc (order param = desc), Asc (order param = asc)
Type - options: All (empty value for API request in mime_types param), Static ("jpg,png" value for API request in mime_types param), Animated ("gif" value for API request in mime_types param)
Breed - options we should get with authorized request from /breeds
Category - options we should get with authorized request from /categories

Interface should be developed in the following manner:
1. we should place search parameters
2. we should place API response with data grid placing images in 3x3 data table
3. we should place the dropdown with 3 options: 9, 18, 80 for limiting records per page and blue button MORE to load more images according to requested parameters

Using all of them we should get Cat images from https://api.thecatapi.com/images/search.
Every API request should be authorized using x-api-key parameter in header request.

Mockup:
![image](https://user-images.githubusercontent.com/107668807/174448306-8d2e023c-a87b-4b36-a9b7-4bd656e65da8.png)
TASK: prepare test cases for testing UI.
