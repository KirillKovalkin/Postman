## HW_2 Postman
### `http://162.55.220.72:5005/first`
### 1. Отправить запрос.
+ **Request**
```js
GET http://162.55.220.72:5005/first
```
+ **Response**
```js
This is the first responce from server!ss
```
### 2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/de5d8a69-b115-4d71-98f6-9d83ddc1417e)

### 3. Проверить, что в body приходит правильный string.
```js
pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/c04f0c1f-8768-45db-a62f-4826d3bb1a1a)

___
### `http://162.55.220.72:5005/user_info_3`
### 1. Отправить запрос.
+ **Request**
```js
POST http://162.55.220.72:5005/user_info_3
age:30
name:"Kirill"
salary:1000
```
+ **Response**
```json
{
    "age": "30",
    "family": {
        "children": [
            [
                "Alex",
                24
            ],
            [
                "Kate",
                12
            ]
        ],
        "u_salary_1_5_year": 4000
    },
    "name": "Kirill",
    "salary": 1000
}
````
### 2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/3a1a3968-83fa-44bf-9d10-3f1612d2ee16)

### 3. Спарсить response body в json.
```js
var resp = pm.response.json();
```
### 4. Проверить, что name в ответе равно name s request (name вбить руками.)
```js
pm.test("Name == name request", function () {
    pm.expect(resp.name).to.eql("Kirill");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/64713c95-71e2-4af2-9e16-840aa1f89ee7)

### 5. Проверить, что age в ответе равно age s request (age вбить руками.)
```js
pm.test("Age == age request", function () {
    pm.expect(resp.age).to.eql("30");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/b9c6780f-44bb-4688-9502-891f0f50504c)

### 6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```js
pm.test("Salary == salary request", function () {
    pm.expect(resp.salary).to.eql(1000);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/ce06857c-8eb2-4f93-8181-5ebaaa2775ad)

### 7. Спарсить request.
```js
var req = request.data
```
### 8. Проверить, что name в ответе равно name s request (name забрать из request.)
```js
pm.test("Name response == name request", function () {
    pm.expect(resp.name).to.eql(req.name);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/92a60109-c7be-4cab-a107-8c67061c2d28)

### 9. Проверить, что age в ответе равно age s request (age забрать из request.)
```js
pm.test("Age response == age request", function () {
    pm.expect(resp.age).to.eql(req.age);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/225793e8-8bba-4da0-9eac-10b63923ed89)

### 10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```js
pm.test("Salary response == salary request", function () {
    pm.expect(resp.salary).to.eql(parseInt(req.salary));
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/184f55f8-c10e-479c-8f81-80562b30d2b9)

### 11. Вывести в консоль параметр family из response.
```js
console.log(resp.family)
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/6ad7a085-5a3c-44de-beff-9f08bf51fda1)

### 12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```js
pm.test("Salary 1.5 year == salary * 4", function () {
    pm.expect(resp.family.u_salary_1_5_year).to.eql(req.salary * 4);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/5745bd3a-af3b-4360-8eee-ed7b1ac38a28)

___
### `http://162.55.220.72:5005/object_info_3`
### 1. Отправить запрос.
+ **Request**
```js
GET http://162.55.220.72:5005/object_info_3
```
+ **Response**
```json
{
    "age": "30",
    "family": {
        "children": [
            [
                "Alex",
                24
            ],
            [
                "Kate",
                12
            ]
        ],
        "pets": {
            "cat": {
                "age": 3,
                "name": "Sunny"
            },
            "dog": {
                "age": 4,
                "name": "Luky"
            }
        },
        "u_salary_1_5_year": 4000
    },
    "name": "Kirill",
    "salary": 1000
}
```
### 2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/2a270a16-7f21-4144-9480-db11cd29e3cb)

### 3. Спарсить response body в json.
```js
var resp = pm.response.json();
```
### 4. Спарсить request.
```js
var req = pm.request.url.query.toObject();
```
### 5. Проверить, что name в ответе равно name s request (name забрать из request.)
```js
pm.test("Name response == name request", function () {
    pm.expect(resp.name).to.eql(req.name);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/9a8f5338-eb0e-421e-997a-70eb10ec986a)

### 6. Проверить, что age в ответе равно age s request (age забрать из request.)
```js
pm.test("Age response == age request", function () {
    pm.expect(resp.age).to.eql(req.age);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/34c8c593-33ca-4cc7-a30c-2835fbf09919)

### 7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```js
pm.test("Salary response == salary request", function () {
    pm.expect(resp.salary).to.eql(parseInt(req.salary));
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/a96da56b-c136-463d-a651-3cee08f062b9)

### 8. Вывести в консоль параметр family из response.
```js
console.log (resp.family)
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/c2d47d7a-21ce-4307-9869-187471e06cdf)

### 9. Проверить, что у параметра dog есть параметры name.
```js
pm.test("Dog contain name", function () {
    pm.expect(resp.family.pets.dog).to.have.property("name");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/4af9f89e-8922-4f27-9ba6-e7cbc25aa416)

### 10. Проверить, что у параметра dog есть параметры age.
```js
pm.test("Dog contain age", function () {
    pm.expect(resp.family.pets.dog).to.have.property("age");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/84c9cd4a-a22b-493b-aa88-7d4ff36a460b)

### 11. Проверить, что параметр name имеет значение Luky.
```js
pm.test("Dog name is Luky", function () {
    pm.expect(resp.family.pets.dog.name).to.eql("Luky");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/962ba3c9-3a38-4df1-b1dc-d47b9f1e6002)

### 12. Проверить, что параметр age имеет значение 4.
```js
pm.test("Dog age is 4", function () {
    pm.expect(resp.family.pets.dog.age).to.eql(4);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/371c24f4-ff5a-4f49-b327-f5b9006db4d8)

___
### `http://162.55.220.72:5005/object_info_4`
1. Отправить запрос.
+ **Request**
```js
GET http://162.55.220.72:5005/object_info_4
```
+ **Response**
```json
{
    "age": 30,
    "name": "Kirill",
    "salary": [
        1000,
        "2000",
        "3000"
    ]
}
```
2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/6c91d7e7-1bd8-4f01-ab42-d4133abb23c4)

3. Спарсить response body в json.
```js
var resp = pm.response.json();
```
4. Спарсить request.
```js
var req = pm.request.url.query.toObject();
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```js
pm.test("Name response == name request", function () {
    pm.expect(resp.name).to.eql(req.name);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/9f3ff3cb-a0d8-4d07-934c-d576277ba0ba)

6. Проверить, что age в ответе равно age из request (age забрать из request.)
```js
pm.test("Age response == age request", function () {
    pm.expect(resp.age).to.eql(parseInt(req.age));
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/13b3c951-ddcd-4d79-bc64-3de5456a164f)

7. Вывести в консоль параметр salary из request.
```js
console.log(req.salary)
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/c3b98f8d-23a9-48b0-a890-548dfe8cc386)

8. Вывести в консоль параметр salary из response.
```js
console.log(resp.salary)
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/1b47211b-7660-4692-b566-99639fb1da16)

9. Вывести в консоль 0-й элемент параметра salary из response.
```js
console.log(resp.salary[0])
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/7f9310c0-c81a-421c-bd3b-4f225da8d864)

10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```js
console.log(resp.salary[1])
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/28da5ae9-8b46-4717-98a4-d4c8c0215b17)

11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```js
console.log(resp.salary[2])
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/1394764e-43cc-4d81-b5b1-05f32f2723ad)

12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```js
pm.test("Salary response [0] == salary request", function () {
    pm.expect(resp.salary[0]).to.eql(parseInt(req.salary));
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/a4345175-c79d-4ad2-8dee-a3f69a2b4686)

13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```js
pm.test("Salary response [1] == salary request * 2", function () {
    pm.expect(parseInt(resp.salary[1])).to.eql(req.salary * 2);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/8fe69543-1069-44f3-8439-20d875fe9531)

14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```js
pm.test("Salary response [2] == salary request * 3", function () {
    pm.expect(parseInt(resp.salary[2])).to.eql(req.salary * 3);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/a60ea57d-0cdf-4dab-a0bc-3cb92a5610e7)

15. Создать в окружении переменную name
```js
pm.environment.get("name");
```
16. Создать в окружении переменную age
```js
pm.environment.get("age");
```
17. Создать в окружении переменную salary
```js
pm.environment.get("salary");
```
18. Передать в окружение переменную name
```js
pm.environment.set("name", resp.name);
```
19. Передать в окружение переменную age
```js
pm.environment.set("age", resp.age);
```
20. Передать в окружение переменную salary
```js
pm.environment.set("salary", resp.salary[2]);
```
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```js
for (var i = 0; i < resp.salary.length; i++){
    console.log("Salary " + i + ": " + resp.salary[i])
}
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/9dd902c4-474e-42c7-8f1e-8d906eaef7ef)

___
### `http://162.55.220.72:5005/user_info_2`
### 1. Вставить параметр salary из окружения в request
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/1f4d2c70-273e-42ac-b079-a826b4467cd9)

### 2. Вставить параметр age из окружения в age
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/97f14466-fdab-4254-a7f8-d796be871b3e)


### 3. Вставить параметр name из окружения в name
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/909e7001-8219-4dfe-ae40-abad9655f4ce)


### 4. Отправить запрос.
+ **Request**
```js
POST http://162.55.220.72:5005/user_info_2
```
+ **Response**
```json
{
    "person": {
        "u_age": 30,
        "u_name": [
            "Kirill",
            3000,
            30
        ],
        "u_salary_5_years": 12600.0
    },
    "qa_salary_after_1.5_year": 9900.0,
    "qa_salary_after_12_months": 8100.000000000001,
    "qa_salary_after_3.5_years": 11400.0,
    "qa_salary_after_6_months": 6000,
    "start_qa_salary": 3000
}
```

### 5. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/a3408d2b-64a4-458e-8b4a-2e9a654243f9)

### 6. Спарсить response body в json.
```js
var resp = pm.response.json();
```
### 7. Спарсить request.
```js
var req = request.data;
```
### 8. Проверить, что json response имеет параметр start_qa_salary
```js
pm.test("Response contain start_qa_salary", function () {
    pm.expect(resp).to.have.property("start_qa_salary");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/a0576557-1dd3-4424-a32b-3ecf0e195f22)

### 9. Проверить, что json response имеет параметр qa_salary_after_6_months
```js
pm.test("Response contain qa_salary_after_6_months", function () {
    pm.expect(resp).to.have.property("qa_salary_after_6_months");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/6656d04b-361d-42bc-ae76-81fbe33887ea)

### 10. Проверить, что json response имеет параметр qa_salary_after_12_months
```js
pm.test("Response contain qa_salary_after_12_months", function () {
    pm.expect(resp).to.have.property("qa_salary_after_12_months");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/5ea6c304-eb9e-402e-b007-54b86701d817)

### 11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```js
pm.test("Response contain qa_salary_after_1.5_year", function () {
    pm.expect(resp).to.have.property("qa_salary_after_1.5_year");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/0e21537d-47b9-4156-88cc-6ae79c0e8cdc)

### 12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```js
pm.test("Response contain qa_salary_after_3.5_years", function () {
    pm.expect(resp).to.have.property("qa_salary_after_3.5_years");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/cf577c36-a669-444d-ba7a-53fcdb8086ca)

### 13. Проверить, что json response имеет параметр person
```js
pm.test("Json response contain person", function () {
    pm.expect(resp).to.have.property("person");
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/fa885c5d-3ad4-47e7-b28d-28dfb6a211de)

### 14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```js
pm.test("Start_qa_salary response == salary request", function () {
    pm.expect(resp.start_qa_salary).to.eql(parseInt(req.salary));
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/11fb735e-d926-4cd6-83e8-3e110fcc2759)

### 15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```js
pm.test("Qa_salary_after_6_months response == salary request * 2", function () {
    pm.expect(resp.qa_salary_after_6_months).to.eql(req.salary * 2);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/a802494b-3aba-4aea-bda3-19d698d1cbfd)

### 16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```js
pm.test("Qa_salary_after_12_months response == salary request * 2.7", function () {
    pm.expect(resp.qa_salary_after_12_months).to.eql(req.salary * 2.7);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/f8285647-5184-45c9-b009-ffd8f3686a07)

### 17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```js
pm.test("Qa_salary_after_1.5_year response равен salary request * 3.3", function () {
    pm.expect(resp["qa_salary_after_1.5_year"]).to.eql(req.salary * 3.3);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/bdc00ecc-8a46-4bc2-ad99-ca39dbde7b9e)

### 18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```js
pm.test("Qa_salary_after_3.5_years response равен salary request * 3.8", function () {
    pm.expect(resp["qa_salary_after_3.5_years"]).to.eql(req.salary * 3.8);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/a18ffcad-5edb-44b2-b17b-a5a7d76f4d82)

### 19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```js
pm.test("person.u_name[1] response == salary request", function () {
    pm.expect(resp.person.u_name[1]).to.eql(parseInt(req.salary));
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/cd56e7dc-7ebc-491c-83f7-4435072285d7)

### 20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```js
pm.test("person.u_age response == age request", function () {
    pm.expect(resp.person.u_age).to.eql(parseInt(req.age));
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/9925c2ce-69bd-4681-91da-c97a0250a5cc)

### 21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```js
pm.test("u_salary_5_years response == salary * 4.2 request", function () {
    pm.expect(resp.person.u_salary_5_years).to.eql(req.salary * 4.2);
});
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/ab2390b4-7ba0-4c82-abc7-2f91c3876654)

### 22. Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```js
for (i in resp.person) {
  console.log(`${i} = ${resp.person[i]}`);
}
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/c112fa7c-ca4e-43d9-a311-9b1e2b833e51)
