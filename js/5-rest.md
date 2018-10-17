# RESTful Api

REST (REpresentational State Transfer) is more a collection of principles for using the HTTP/HTTPS protocols.

The six constraints of REST are:
- Uniform Interface (clear usage rools)
- Stateless (the state is inside the url itself)
- Cacheable (the response can be cached)
- Client-Server
- Layered System (intermediate servers can be used with no client overhead)
- Code on Demand (providing frontend code by the backend)

## Example
base url: users
get all users: users (GET)
get one user users/id (GET)
add a user: users (POST - {name: 'Pesho', age: 19...})
edit a user: users/id (PATCH - {id: id, age: 20})
edit a user: users/id (PUT - {id: id, name: 'Pesho', age: 20})
delete a user: users/id (DELETE)
search for a user: users?name=Pesho

## Details
- DRY (do not repeat yourself)
- the results are returned in json or xml

## Results
{"code":200,"status":"success","data": [{...}, ...]}
{"code":401,"status":"error","message":"token is invalid","data":"UnauthorizedException"}

## CORS
Server header: Access-Control-Allow-Origin: *
OPTION requests

## Learn more
- [Rest Tutorial](https://github.com/tfredrich/RestApiTutorial.com/raw/master/media/RESTful%20Best%20Practices-v1_2.pdf)
- [CORS](https://enable-cors.org/index.html)