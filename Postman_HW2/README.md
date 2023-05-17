## HW_2 Postman
### `http://162.55.220.72:5005/first`
### 1. Отправить запрос.
+ **Request**
```js
GET http://162.55.220.72:5005/first
```
![image](https://github.com/KirillKovalkin/Postman/assets/108697657/5e7c5dda-7403-4abe-9bbb-bc9c23f5417c)

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
```js
POST http://162.55.220.72:5005/user_info_3
age:30
name:"Kirill"
salary:1000
```
### 2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
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
### 5. Проверить, что age в ответе равно age s request (age вбить руками.)
```js
pm.test("Age == age request", function () {
    pm.expect(resp.age).to.eql("30");
});
```
### 6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```js
pm.test("Salary == salary request", function () {
    pm.expect(resp.salary).to.eql(1000);
});
```
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
### 9. Проверить, что age в ответе равно age s request (age забрать из request.)
```js
pm.test("Age response == age request", function () {
    pm.expect(resp.age).to.eql(req.age);
});
```
### 10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```js
pm.test("Salary response == salary request", function () {
    pm.expect(resp.salary).to.eql(parseInt(req.salary));
});
```
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
http://162.55.220.72:5005/object_info_3
1. Отправить запрос.
2. Статус код 200
3. Спарсить response body в json.
4. Спарсить request.
5. Проверить, что name в ответе равно name s request (name забрать из request.)
6. Проверить, что age в ответе равно age s request (age забрать из request.)
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
8. Вывести в консоль параметр family из response.
9. Проверить, что у параметра dog есть параметры name.
10. Проверить, что у параметра dog есть параметры age.
11. Проверить, что параметр name имеет значение Luky.
12. Проверить, что параметр age имеет значение 4.

http://162.55.220.72:5005/object_info_4
1. Отправить запрос.
2. Статус код 200
3. Спарсить response body в json.
4. Спарсить request.
5. Проверить, что name в ответе равно name s request (name забрать из request.)
6. Проверить, что age в ответе равно age из request (age забрать из request.)
7. Вывести в консоль параметр salary из request.
8. Вывести в консоль параметр salary из response.
9. Вывести в консоль 0-й элемент параметра salary из response.
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
15. Создать в окружении переменную name
16. Создать в окружении переменную age
17. Создать в окружении переменную salary
18. Передать в окружение переменную name
19. Передать в окружение переменную age
20. Передать в окружение переменную salary
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.

http://162.55.220.72:5005/user_info_2
1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name
4. Отправить запрос.
5. Статус код 200
6. Спарсить response body в json.
7. Спарсить request.
8. Проверить, что json response имеет параметр start_qa_salary
9. Проверить, что json response имеет параметр qa_salary_after_6_months
10. Проверить, что json response имеет параметр qa_salary_after_12_months
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
13. Проверить, что json response имеет параметр person
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
