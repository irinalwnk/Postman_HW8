# Postman_HW8
HW_2 Postman


http://162.55.220.72:5005/first
1. Отправить запрос.   
	`Выбираем метод Get.`  
	`В URL копируем http://162.55.220.72:5005/first`     
	`Сохраняем и посылаем запрос.`  
	
2. Статус код 200  
	`Переходим во вкладку Tests.`    
	`В меню справа выбираем Status code: Code is 200.`    
	``` JSON pm.test("first Статус код 200", function () {  
  	  pm.response.to.have.status(200);  
	});```  
	`В нижнем меню выбираем вкладку Test Results.`    
	`Сохраняем и посылаем запрос.`    
	`Проверяем результат теста:`    
	`PASS first Статус код 200`   

3. Проверить, что в body приходит правильный string.  
	`Во вкладке Body проверяем ответ сервера:`    
	`This is the first responce from server!`    


http://162.55.220.72:5005/user_info_3  
1. Отправить запрос.  
	`Выбираем метод Get.`  
	`В URL копируем http://162.55.220.72:5005/user_info_3`
	`Во вкладке Body ставим галочку form-data.`  
	`Вносим необходимые Key и Value:`  
	`name : Alex`  
	`age: 32`  
	`salary: 2000`  
	`Сохраняем и посылаем запрос.`  

2. Статус код 200  
	`Переходим во вкладку Tests.`    
	`В меню справа выбираем Status code: Code is 200.`    
	``` JSON pm.test("user_info_3 Статус код 200", function () {  
  	  pm.response.to.have.status(200);  
	});```  
	`Сохраняем и посылаем запрос.`  
	`В нижнем меню выбираем вкладку Test Results.`    
	`Проверяем результат теста:`    
	`PASS first Статус код 200`   
 
3. Спарсить response body в json.  
	`Переходим во вкладку Tests.`   
	`Из списка справа выбираеем:`  
	`Response body: JSON value check`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	 let jsonData = pm.response.json();`   
	 console.log(jsonData); ```    
	`Проверяем содержимое переменной, выводя ее в Console:`  	
	`{age: "32", family: {…}, name: "Alex"…}`  

4. Проверить, что name в ответе равно name s request (name вбить руками.)
	`Во вкладке Tests.`   
	`Из списка справа выбираеем:`  
	`Response body: JSON value check`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	let ResponseData = pm.response.json();  
	pm.test("name в ответе равен name в запросе", function () {  
	pm.expect(ResponseData.name).to.eql("Alex");`  
	});```  
	`Сохраняем и посылаем запрос.`  
	`Проверяем результат теста:` 
	`PASS name в ответе равен name в запросе`  
 	
5. Проверить, что age в ответе равно age s request (age вбить руками.)  
	`Во вкладке Tests.`   
	`Из списка справа выбираеем:`  
	`Response body: JSON value check`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("age в ответе равен age в запросe", function () {  
	pm.expect(ResponseData.age).to.eql("32");`  
	});```  
	`Сохраняем и посылаем запрос.`  
	`Проверяем результат теста:` 
	`PASS age в ответе раве age в запросе`  

6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
	`Во вкладке Tests.`   
	`Из списка справа выбираеем:`  
	`Response body: JSON value check`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("salary в ответе раве salaty в запросe", function () {  
	pm.expect(ResponseData.salary).to.eql(2000);`  
	});```  
	`Сохраняем и посылаем запрос.`  
	`Проверяем результат теста:` 
	`PASS salary в ответе равен salary в запросе`  

7. Спарсить request.
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	let RequestData = request.data;  
	console.log('request data:', RequestData)```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем содержимое переменной, выводя ее в Console:`  	
	`request data: {name: "Alex", age: "32", salary: "2000"}`  
	
8. Проверить, что name в ответе равно name s request (name забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("значения ключей name в ответе и в запросе совпадают", function () {  
	pm.expect(ResponseData.name).to.eql(RequestData.name);  
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS значения ключей name в ответе и в запросе совпадают`  	

9. Проверить, что age в ответе равно age s request (age забрать из request.)
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("значения ключей age в ответе и в запросе совпадают", function () {
	pm.expect(ResponseData.age).to.eql(RequestData.age);  
	});```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS значения ключей age в ответе и в запросе совпадают`  

10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	pm.test("значения ключей salary в ответе и в запросе совпадают", function () {  
	pm.expect(ResponseData.salary).to.eql(+RequestData.salary);  
	/* или  
	pm.expect(ResponseData.salary).to.eql(Number(RequestData.salary)); */  
	});```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS значения ключей age в ответе и в запросе совпадают`  

11. Вывести в консоль параметр family из response.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	 console.log('Family:', ResponseData.family)```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат в Console:` 
	`Family:`  
	`{children: [2], u_salary_1_5_year: 8000}`  
	`children: [2]`    
	`u_salary_1_5_year: 8000`    
	
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	pm.test("u_salary_1_5_year в ответе равно salary*4", function () {  
	pm.expect(ResponseData.family.u_salary_1_5_year).to.eql(+RequestData.salary*4);   
	});   ```    
	`Сохраняем и посылаем запрос.` 		
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS u_salary_1_5_year в ответе равно salary*4`  

http://162.55.220.72:5005/object_info_3  
1. Отправить запрос.  
	`Выбираем метод Get.`  
	`В URL копируем http://162.55.220.72:5005/object_info_3`  
	`Во вкладке Params :`    
	`Вносим необходимые Key и Value:`  
	`name : Alex`  
	`age: 32`  
	`salary: 2000`  
	`Сохраняем и посылаем запрос.`  

2. Статус код 200  
	`Переходим во вкладку Tests.`    
	`В меню справа выбираем Status code: Code is 200.`    
	``` JSON   
	pm.test("user_info_3 Статус код 200", function () {  
  	  pm.response.to.have.status(200);  
	});```  
	`Сохраняем и посылаем запрос.`  
	`В нижнем меню выбираем вкладку Test Results.`    
	`Проверяем результат теста:`    
	`PASS object_info_3 Статус код 200`   

3. Спарсить response body в json.  
	`Переходим во вкладку Tests.`   
	`Из списка справа выбираеем:`  
	`Response body: JSON value check`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	 let ResponseBody =  pm.response.json();  
	 console.log('Response Body:', ResponseBody); ```    
	`Проверяем содержимое переменной, выводя ее в Console:`  	
	` Response Body: {age: "32", family: {…}, name: "Alex"…}`  

4. Спарсить request.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	let RequestData = pm.request.url.query.toObject();  
	console.log('Request Data: ', RequestData);```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем содержимое переменной, выводя ее в Console:`  	
	`request data: {name: "Alex", age: "32", salary: "2000"}`   
 
5. Проверить, что name в ответе равно name s request (name забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("name в ответе равен name в запросе", function () {  
	pm.expect(ResponseData.name).to.eql(RequestData.name);  
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS name в ответе равен name в запросе`  	

6. Проверить, что age в ответе равно age s request (age забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("age в ответе равен age в запросе", function () {  
	pm.expect(ResponseData.age).to.eql(RequestData.age);  
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS age в ответе равен age в запросе`     
 
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("salary  в ответе равен salary в запросе", function () {  
	pm.expect(ResponseData.salary ).to.eql(RequestData.salary );  
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS salary в ответе равен salary в запросе` 
    
8. Вывести в консоль параметр family из response.
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	 console.log('Family:', ResponseBody.family);```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат в Console:` 
	`Family: {children: [2], pets: {…}, u_salary_1_5_year: 8000}`  
 
9. Проверить, что у параметра dog есть параметры name.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	pm.test("dog has a name", function () {  
	pm.expect(ResponseBody.family.pets.dog).to.haveOwnProperty('name');   
	});   ```    	
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS dog has a name`  

10. Проверить, что у параметра dog есть параметры age.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	pm.test("dogs name is Luky", function () {   
	pm.expect(ResponseBody.family.pets.dog.name).to.eql('Luky');   
	});   ```    	
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS dogs name is Luky` 

11. Проверить, что параметр name имеет значение Luky.   
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	pm.test("dog has an age", function () {  
	pm.expect(ResponseBody.family.pets.dog).to.haveOwnProperty('age');   
	});   ```    	
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS dog has a name` 

12. Проверить, что параметр age имеет значение 4.   
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	pm.test("параметр age имеет значение 4", function () {  
	pm.expect(ResponseBody.family.pets.dog.age).to.eql(4);   
	});    ```    	
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS dog has a name` 

http://162.55.220.72:5005/object_info_4  
1. Отправить запрос.  
	`Выбираем метод Get.`  
	`В URL копируем hthttp://162.55.220.72:5005/object_info_4`  
	`Во вкладке Params :`    
	`Вносим необходимые Key и Value:`  
	`name : Alex`  
	`age: 32`  
	`salary: 2000`  
	`Сохраняем и посылаем запрос.`  
2. Статус код 200  
	`Переходим во вкладку Tests.`    
	`В меню справа выбираем Status code: Code is 200.`    
	``` JSON   
	pm.test("object_info_3 Статус код 200", function () {  
	pm.response.to.have.status(200);  
	});```  
	`Сохраняем и посылаем запрос.`  
	`В нижнем меню выбираем вкладку Test Results.`    
	`Проверяем результат теста:`    
	`PASS object_info_4 Статус код 200`  

3. Спарсить response body в json.  
	`Переходим во вкладку Tests.`   
	`Из списка справа выбираеем:`  
	`Response body: JSON value check`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	 let ResponseBody =  pm.response.json();  
	 console.log('Response Body:', ResponseBody); ```    
	`Проверяем содержимое переменной, выводя ее в Console:`  	
	`Response Body: {age: 32, name: "Alex", salary: [3]}`   
 
4. Спарсить request.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	let RequestData = pm.request.url.query.toObject();  
	console.log('Request Data: ', RequestData);```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем содержимое переменной, выводя ее в Console:`  	
	`Request Data: {name: "Alex", age: "32", salary: "2000"}`   
 
5. Проверить, что name в ответе равно name s request (name забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("name в ответе равен name в запросе", function () {    
	pm.expect(ResponseBody.name).to.eql(RequestData.name);  
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS name в ответе равен name в запросе`  	

6. Проверить, что age в ответе равно age из request (age забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("age в ответе равен age в запросе", function () {  
	pm.expect(ResponseBody.age).to.eql(+RequestData.age);  
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS age в ответе равен age в запросе`   

7. Вывести в консоль параметр salary из request.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	 console.log('salary from Request:', RequestData.salary);```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат в Console:` 
	`salary from Request: 2000`  
    
8. Вывести в консоль параметр salary из response.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	 console.log('salary:', ResponseBody.salary);```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат в Console:` 
	`salary:(3) [2000, "4000", "6000"]`  

9. Вывести в консоль 0-й элемент параметра salary из response.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	 console.log('salary element 0:', ResponseBody.salary[0]);```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат в Console:` 
	`salary element 0: 2000`  

10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	 console.log('salary element 1:', ResponseBody.salary[1]);```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат в Console:` 
	`salary element 1: "4000"`  

11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON   
	 console.log('salary element 2:', ResponseBody.salary[2]);```    
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат в Console:` 
	`salary element 1: "6000"`  

12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("salary  в ответе равен salary в запросе", function () {  
	pm.expect(ResponseBody.salary[0]).to.eql(+RequestData.salary);    
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS salary в ответе равен salary в запросе` 
    
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)  
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("salary element 2 equal salary*3 request", function () {  
	pm.expect(+ResponseBody.salary[2]).to.eql(RequestData.salary*3);  
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS salary element 1 equal salary*2 request` 

14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
	`Во вкладке Tests.`   
	`В окне редактирования тестов оставляем код:`   
	```JSON  
	pm.test("salary element 2 equal salary*3 request", function () {    
	pm.expect(+ResponseBody.salary[2]).to.eql(RequestData.salary*3);    
	});```  
	`Сохраняем и посылаем запрос.` 		
	`Проверяем результат теста:` 
	`PASS salary element 2 equal salary*3 request` 

15. Создать в окружении переменную name  
	`Слева в меня выбирать Environment - New`  
	`В строку Variable внести название переменной name`  
	`Сохранить`  

16. Создать в окружении переменную age
	`Слева в меня выбирать Environment - New`  
	`В строку Variable внести название переменной age`  
	`Сохранить`  

17. Создать в окружении переменную salary
	`Слева в меня выбирать Environment - New`  
	`Назвать новое окружение HW_8`  
	`В строку Variable внести название переменной salary`  
	`Сохранить`  

18. Передать в окружение переменную name 
	`Перейти во вкладку Tests`  
	`Вверху справа выбрать Environment - HW_8`  
	`В окне редактирования тестов оставляем код:`  
	```JSON 
	pm.environment.set("name", ResponseBody.name);```  
	`Сохранить и передать запрос`  

19. Передать в окружение переменную age  
	`В окне редактирования тестов оставляем код:`  
	```JSON 
	pm.environment.set("age", ResponseBody.age);```  
	`Сохранить и передать запрос`  

20. Передать в окружение переменную salary
	`В окне редактирования тестов оставляем код:`  
	```JSON 
	pm.environment.set("salary", ResponseBody.salary);```  
	`Сохранить и передать запрос`  

21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.  
	`В окне редактирования тестов оставляем код:`  
	```JSON  
	for (let i of ResponseBody.salary) {  
	console.log('Elements of salary:',i);  
    	}```  
	`Сохранить и передать запрос` 
	`Проверяем результат в Console:`  
	`Elements of salary:`  
	`2000`  
	`Elements of salary:`  
	`4000`  
	`Elements of salary:`  
	`6000`  


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
