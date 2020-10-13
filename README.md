# javascript-and-angular-interview-questions

JavaScript and Angular Interview Questions &amp; Answers

## Содержание

| № | Questions |
|---- | ---------
| I| [Основы](#Основы) |
| 1| [Чистота функции](#чистота-функции) |
| 2| [Что такое императивное программирование](#что-такое-императивное-программирование) |
| 3| [Что такое декларативное программирование](#что-такое-декларативное-программирование) |
| 4| [Что такое функция высшего порядка](#что-такое-функция-высшего-порядка) |
| 5| [Функциональное программирование](#Функциональное-программирование) |
| 6| [Реактивное программирование](#Реактивное-программирование) |
| 7| [Методологии разработка](#Методологии-разработка) |
| 8| [ООП](#ООП) |
| 9| [SOLID](#SOLID) |
| II| [JavaScript](#JavaScript) |
| 1| [Типы данных](#Типы-данных) |
| 2| [Область видимости](#область-видимости) |
| 3| [Lexical environment](#Lexical-environment) |
| 4| [Замыкание](#Замыкание) |
| 5| [Hoisting](#Hoisting) |
| 6| [Разница между function expression и function declaration](#Разница-между-function-expression-и-function-declaration) |
| 7| [Способы создать объект](#Способы-создать-объект) |
| 8| [this](#this) |
| 9| [Что такое цепочка прототипов](#Что-такое-цепочка-прототипов) |
| 10| [Разница между for in и for of](#Разница-между-for-in-и-for-of) |
| 11| [Разница между методами массива slice и splice](#Разница-между-методами-массива-slice-и-splice) |
| 12| [Разница между == и ===](#Разница-между-==-и-===) |
| 13| [Каррирование](#Каррирование) |
| 14| [Разница между let и var](#Разница-между-let-и-var) |
| 15| [Что такое временная мертвая зона](#Что-такое-временная-мертвая-зона) |
| 16| [Классы в es6](#Классы-в-es6) |
| 17| [Что такое деструктуризация](#Что-такое-деструктуризация) |
| 18| [Способы привязать контекста к функции](#Способы-привязать-контекста-к-функции) |
| 19| [Прототипное наследование](#Прототипное-наследование) |
| 20| [Функциональное наследование](#Функциональное-наследование) |
| 21| [Назначение super в классе](#Назначение-super-в-классе) |
| 22| [Разница между obj.\_\_proto__ и obj.Prototype](#Разница-между-obj.\_\_proto__-и-obj.Prototype) |

## Основы

1. ### Чистота функции
 
      ***Чистая функция*** - это функция, которой присущи следующие характеристики:
      - Принимает на вход аргументы.
      - При одних и тех же аргументах возвращает одни и те же значения.
      - Не меняет внешний контекст
      - Не вызывает нечистые функции
      - Не имеет побочных эффектов.
      
      ##### Пример: 
      
           function getWordCount(arr) {   
	   	return arr.length;    // этой функции присущи все вышеобозначенные характеристики
	   }
	   
	   
      ***Нечистая функция*** - это функция, которой, соответственно, обозначенные выше характеристики не присущи.
   
      К ***побочным эффектам*** функции относят вызовы API, манипулирование DOM-ом, запись в базу данных, чтение и модификация глобальных переменных.

2. ### Что такое императивное программирование

      ***Императивное программирование*** - это способ написания кода, в котором фокусом есть *описание логики* работы программы. К такому коду можно поставить вопрос **"Как именно мы что-то делаем?"**. 
      ##### Пример: 
      Нужно написать функцию, которая принимает массив, а возвращает сумму значений массива. Императивным подходом это решается следующим образом: 
      
          function add(arr) {
            let result = 0;
            for(let i = 0; i < arr.length; i++) {
              result +=arr[i];
            }
            return result;
          }
      
      Как видно из примера - мы описали как именно мы достигаем решения поставленной задачи (сначала у нас результат 0, потом проходимся по массиву, потом возвращаем результат). 

3. ### Что такое декларативное программирование
      ***Декларативное программирование*** - это способ написания кода, в котором фокусом есть *указание результата*, который мы хотим получить. К такому коду можно поставить вопрос **"Что именно мы получаем?"**
      #### Пример: 
      Задача стоит такая же, как и в предыдущем пункте. Декларативным подходом это решается следующим образом: 
      
          function add(arr) {
            return arr.reduce((prev, current) => prev + current, 0);
          }
      
      Как видно из примера - мы пишем ***ЧТО*** мы хотим получить, и не задумываемся, как именно оно получится. Но, понятное дело, что под этой декларативной записью скрывается что-то императивное, но оно скрыто. 
      
      Ссылка на статью, где приводятся аналогии с реальной жизнью: https://ui.dev/imperative-vs-declarative-programming/
4. ### Что такое функция высшего порядка
   ***Функция высшего порядка*** - это функция, которая принимает на вход другие функции, или же возвращает другие функции.
   #### Примеры: 
          function sayHi() {
             alert('Hi!');
          }
      
          function greet(greeting) {
             greeting();
          } 
      
          greet(sayHi); // передаём функцию sayHi в качестве аргумента функции greet.
      
      а также: 
      
          function whenMeetingJohn() { 
            return function() {           
             alert('Hi!);
            }
          }
      
         let atLunchToday = whenMeetingJohn(); 
         atLauchToday(); 
	 
5. ### Функциональное программирование 
      ***Функциональное программирование*** - это одна из парадигм программирования, которая базируется на следующих принципах:
     
      - основные функции реализованы с **использованием чистых функций без побочных эффектов**
      - **данные не изменяются**
      - функциональные программы **не имеют состояния**
      - императивный код **контейнера (нечистая функция) управляет побочными эффектами и выполняет декларативный**, чистый код ядра.
         
   #### Пример:
   
          const fpCopy = `Functional programming is powerful and enjoyable to write. It's very cool!`;
          
          // все функции, кроме последней - чистые. Не изменяют никакие данные.
          const stripPunctuation = (str) => str.replace(/[.,\/#!$%\^&\*;:{}=\-_`~()]/g, '');
          
          const getArr = (str) => str.split(' ');
          
          const getWordCount = (arr) => arr.length;
          
          const getKeywords = (arr) => arr
               .filter(item => item.length > 5)
               .map(item => item.toLowerCase());
               
          // это контейнер, который является нечистой функцией. Управляет побочными эффектами и выполняет предыдущие чистые функции
          function processCopy(str, prepFn, arrFn, countFn, kwFn) {
            const copyArray = arrFn(prepFn(str));
            return `Word count: ${countFn(copyArray)}, keywords: ${kwFn(copyArray)}`;
          }
           processCopy(fpCopy, stripPunctuation, getArr, getWordCount, getKeywords);
    
    
6. ### Реактивное программирование 
      ***Реактивное программирование*** - это парадигма программирования, которая заключается в декларативным наблюдением и реагированием на поступающие события во времени. 
7. ### Методологии разработка
   1. Agile
      * экстремальное программирование (Extreme Programming, XP); <br>
      ***Цель*** - справиться с постоянно меняющимися требованиями к программному продукту и повысить качество разработки. 4 принципа:

         1) **Кодирование** согласно единым в команде стандартам оформления. 
         2) **Тестирование**. Тесты пишут сами программисты ещё до написания кода, который будут тестировать. 
         3) **Планирование**. И финальное и отдельных итераций. (В среднем раз в две недели)
         4) **Слушание**. И разработчиков, и клиента. Цель - устранить неясности и недопонимания, определить четкие требования и ценности.

      * бережливая разработка программного обеспечения (Lean);
      ***Цель*** - повышение эффективности процесса разработки, минимизация затрат. 
	
         1) **Избавление от потерь** (плюс к качеству). Если что-то не нужно, то его лучше убрать. 
         2) **Постоянное обучение команды (плюс к эффективности)**
         3) **Принятие решения так поздно, как только можно.** Решения должны быть продуманными и взвешенными. (плюс к эффективности и качеству)
         4) **Быстрая доставка**
         5) **Усиление команды.** “Люди и взаимодействие важнее процессов и инструментов”. То, как люди в команде могут взаимодействовать и кооперироваться - важнее даже того, какие инструменты они используют. (плюс к эффективности)
         6) **Целостность и качество.** Изначально нужно делать качественный продукт, то есть не избавляться от проблем и багов, а пресечь их появление (плюс и к эффективности, и к качеству). + **Видение цельной картины.** Нужно чётко понимать, какой текущий статус разработки, какие цели, концепции и стратегии у разрабатываемого ПО
      * фреймворк для управления проектами Scrum;
       
      ***Scrum*** - методология управления проектами, сутью котого есть постоянная вовлеченность в процесс разработки кроме специалистов ещё и владельца продукта (человек, который соединяет команду с заказчиком, мониторит развитие проекта) + scrum-master (человек, который проыводит совещания, мотивирует команду, мониторит соблюдение самого scrum). По Scrum рабочий процесс делится на спринты (некоторые промежутки времени, от недель до месяца). Каждый раз перед началом нового спринта формулируются цели и задачи, которые нужно достичь/решить, в конце каждого спринта обсуждаются результаты, успехи либо фейлы. Что удобно - можно сравнивать эти самые спринты, оценивать эффективной работы, ею управлять.   
      * разработку, управляемую функциональностью (Feature-driven development, FDD);
      * разработку через тестирование (Test-driven development, TDD); <br> 
       Методология разработки ПО, которое основывается на повторении коротких циклов разработки:
         1) Пишется тест, который покрывает нужные изменения;
         2) Пишется код, который желаемые изменения, собственно, реализует и позволяет пройти тест. 
         3) Проводится рефакторинг написанного кода.
	    
      * методология «чистой комнаты» (Cleanroom Software Engineering); <br> 
       Процесс разработки программного обеспечения, который предназначен для создания ПО с сертифицируемым уровнем надежности. Основной принцип: предупреждение проблем (дефектов) лучше, чем их устранение. <br> 
       Основан на следующем: 
         1) Разработка ПО основывается на формальных методах;
         2) Инкрементальная реализация в рамках статистического контроля качества.
         3) статистическое тестирование;
         4) формальная верификация. 
	    
      * итеративно-инкрементальный метод разработки (OpenUP); <br>
        Метод разработки, который делит цикл проекта на четыре фазы: 
         1) Начальная фаза
         2) Фаза уточнения
         3) Фаза конструирования
         4) Фаза передачи. 
	    
      * методологию разработки Microsoft Solutions Framework (MSF); <br>
        Методология, которая базируется на 8 принципах:
         1) Cвободный и открытый обмен инфой между участников внутри команды и заинтересованными сторонами. (снижает вероятность недопонимания и переделывания работы) 
         2) Общий взгляд участников команды на результат, понимание в равной степени всеми целей и задач, над которыми ведётся работа.
         3) Каждый участник обладает максимально полными полномочиями, которые нужны для выполнения задачи.
         4) Разделение ответственности. Все успехи и неудачи команды делятся поровну.
         5) Ориентировка на клиента, на его потребности.
         6) Готовность к переменам требований, условий.
         7) Раннее выявление ошибок и недочетов, которое реализуется на протяжении всего проекта.
         8) Развитие сотрудников, обмен информацией и опытом.
	    
      * метод разработки динамических систем (Dynamic Systems Development Method, DSDM); <br>
        Метод разработки, который основан на концепции быстрой разработки приложений.
        9 принципов DSDM: <br>
          1) Вовлечение пользователя. Для более точного принятия решения разработчики делят с пользователями рабочее пространство.
          2) Необходимость, чтобы команда могла самостоятельно принимать решения (без предварительного согласования с начальством)
          3) Принцип "лучше сделать раньше, но просто хорошо, чем отлично, но в самом конце"
          4) Быстрая доставка ПО, которое удовлетворяет текущим потребностям рынка.
          5) Итеративная (т.е такая, которая происходит с непрерывным анализом полученных результатов и коректировкой предыдущей работы) и инкреметная разработка
          6) любые изменения во время разработки обратимы. 
          7) требования формулируются на высоком уровне прежде, чем начнётся проект.
	  8) в жизненный цикл разработки обязательно интегрируется тестирование.
	  9) крайне необходимо взаимодействие и сотрудничество между всеми учасниками (плюс к эффективности)
	  
      * метод управления разработкой Kanban. <br>
	Kanban держится на 4 столбах: <br>
          1) "Карточки". Для каждой задачи - отдельная карточка, где записана вся необходиммая инфа.
          2) Ограниченное количество задач на одном этапе.
          3) Непрерывный поток.
          4) Постоянное улучшение и совершенствование. ТО есть постоянный и непрерывный анализ производственного процесса + поиск путей дял повышения производительности. 
        
   2. ***Waterfall*** (или же каскадная модель) - модель процесса разработки, которая делит создание проекта на несколько частей (а именно анализ требований, проектирование, реализация, тестирование, интеграция и поддержка), которые следуют один за другим (как поток). Суть в том, что один этап разработки **не может начаться**, пока не завершится другой. Основные принципы - **строгая последоватеьность** и **однократное выполнение** каждоого этапа.
      
   3. ***Спиральная модель*** - модель разработки ПО, которая сочетает идеи итеративной и каскадной моделей. Создание проекта также делится на этапы, но (поскольку у нас спиральная модель) эти этапы повторяются на каждом новом "витке". Просто на выходе с каждого "витка" мы получаем протестированный "прототип", который дополняет существующий билд и дальше начинаются те же этапы и т.д, до тех пор, пока не получим прототип, который удовлетворяет всем требованиям. 
8. ***ООП*** - парадигма программирования, в которой основными концепциями являются понятия объектов и классов. 
   Базовыми принципами ООП есть следующие:
      1. **Абстрагирование**. Означает, что нужно выделить некий набор характеристик объекта. Характеристики должны быть значимыми. **Абстракция**, в свою очередь - это набор значимых характеристих объекта. 
      2. **Инкапсуляция**. То, что помогает "защитить" жизненно важные данные для компонента, а также скрыть детали реализации от пользователя. Но последний, в свою очередь, может взаимодействовать с компнентом при помощи некоего интерфейса.   
      3. **Наследование**. Способность объекта или класса базироваться на другом объекте или классе, способность одного объекта приобретать свойства другого, добавлять к ним что-то, что характерно только для него. Через наследование чётко видна их иерархия.
      4. **Полиморфизм**. Реализация одной и той же задачи разными способами.
      
      Также используются правило **DRY (Don't repeat yourself)**, то есть правило того, что каждая инфа, кадый кусочек кода должен быть представлен в единственном числе в одном месте программмы + принципы **SOLID**. 
9. ### SOLID
   ***SOLID*** - это набор из 5 принципов (сам термин - это акроним из названий этих принципов), который помогает делать код как-будто действительно очень устойчивым и крепким (а слово "solid" с англ так и переводится), читай хорошо организованным, понятным и поддерживаемым, там, где уж точно какое-то изменение в дальнейшем не будет иметь результатом полный крах всего :).  
   Итак, эти принципы: 
   - **Single Responsibility Principle (принцип персональной ответственности)**
   Класс должен иметь лишь одну ответственность, то есть должен отвечать только за одну вещь, на него возложена одна единственная обязанность. Другими словами, Do one thing and do it well!
   - **Open/Closed Principle (Принцип открытости/закрытости)**
   Программные сущности должны быть открыты для расширения, но закрыты для изменения. 
   Иными словами, следует создавать классы таким образом, чтобы со временем можно было дополнить их функционал, но при этом не нужно было затрагивать старый код. Эффективно и быстрее писать новое, расширять уже существующее, при этом не пересматривая и не переделывая уже написанное. 
   - **Liskov Substitution Principle**
   Объекты в программе должны быть заменяемыми на экземпляры их подтипов без изменения правильности выполнения программы.
   - **Interface Segregation Principle.**
   Клиенты не должны зависеть от методов, которые они не используют. 
   - **Dependency Inversion Principle**
   Модули верхних уровней не должны зависеть от модулей нижних уровней. Оба типа модулей должны зависеть от абстракций. Абстракции не должны зависеть от деталей. Детали должны зависеть от абстракций. 
   
   3 статьи, где объясняются эти 5 принципов: 
   
    * https://webdevblog.ru/solid-principy-chast-1/ (1 и 2 принципы).
    * https://webdevblog.ru/solid-principy-chast-2/ (3 принцип).
    * https://webdevblog.ru/solid-principy-chast-3/ (4 и 5 принцип).


## JavaScript

1. ### Типы данных
2. ### Область видимости
3. ### Lexical environment
4. ### Замыкание
5. ### Hoisting
6. ### Разница между function expression и function declaration
7. ### Способы создать объект
8. ### this
9. ### Что такое цепочка прототипов
10. ### Разница между for in и for of
11. ### Разница между методами массива slice и splice
12. ### Разница между == и ===
13. ### Каррирование
14. ### Разница между let и var
15. ### Что такое временная мертвая зона
16. ### Классы в es6
17. ### Что такое деструктуризация
18. ### Способы привязать контекста к функции
19. ### Прототипное наследование
20. ### Функциональное наследование
21. ### Назначение super в классе
22. ### Разница между obj.\_\_proto__ и obj.Prototype

