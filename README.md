# interview-questions



Q. what is tight coupling explain in simple way
### 🔒 What is Tight Coupling? (Simple Explanation)

**Tight coupling** means that **one class is heavily dependent on another class’s exact implementation**.

In simple words:

> 🧱 "If Class A **knows too much** about Class B and **can’t work without it**, they are tightly coupled."

---

### 👎 Example of Tight Coupling

```ts
class Engine {
  start() {
    console.log('Engine started');
  }
}

class Car {
  private engine: Engine;

  constructor() {
    this.engine = new Engine(); // 🔒 Tight coupling: Car creates its own Engine
  }

  drive() {
    this.engine.start();
    console.log('Car is driving');
  }
}
```

#### Why is this bad?

* **You can't easily replace `Engine` with a different one (e.g., `ElectricEngine`)**
* **Hard to test** because `Car` always uses a real `Engine`
* **Changes in `Engine` can break `Car`**

---

### 👍 Loose Coupling (Using Dependency Injection)

```ts
class Engine {
  start() {
    console.log('Engine started');
  }
}

class Car {
  constructor(private engine: Engine) {} // Engine is passed in, not created

  drive() {
    this.engine.start();
    console.log('Car is driving');
  }
}

// Usage
const engine = new Engine();
const car = new Car(engine); // 🔓 Loosely coupled
```

#### Benefits of Loose Coupling:

* **Easy to swap** `Engine` with `ElectricEngine`, `MockEngine`, etc.
* **Easy to test** because you can pass a fake or mock engine
* **More flexible and maintainable**

---

### 🚗 Real-Life Analogy

Imagine a TV remote **only works with one brand of batteries**, and you **can't change them**. That’s tight coupling.

Now imagine a remote that **accepts any brand of AA batteries** — you can swap, test, or upgrade easily. That’s loose coupling.

---

Would you like a visual diagram or analogy using Angular components/services?


| Without DI (Manual)   | With DI (Angular)                            |
| --------------------- | -------------------------------------------- |
| `new LoggerService()` | `constructor(private logger: LoggerService)` |
| Tight coupling        | Loose coupling                               |
| Hard to test          | Easy to test/mock                            |
| Hard to maintain      | Scalable and clean                           |

....................................


 theoretical and practical questions


Q. how to pass the multiple api with same id 
ans:-
 const apiUrls = [
  'https://api.example.com/endpoint1',
  'https://api.example.com/endpoint2',
  'https://api.example.com/endpoint3',
  // ...more API endpoints
];

const commonId = '12345'; // Same ID to pass

const makeRequests = async () => {
  try {
    const responses = await Promise.all(
      apiUrls.map(url => fetch(`${url}?id=${commonId}`)) // Adding the ID to each request
    );

    const results = await Promise.all(responses.map(res => res.json()));
    console.log(results); // Handle the results from all APIs
  } catch (error) {
    console.error('Error in making requests:', error);
  }
};

makeRequests();



????????????????????????????????????????????????
install the node js version 16
angular 16
download vs code
install the tailwindcss
install bootstrap


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Accenture(28-feb-2026)

1. how to know the when ngDestroy is called in project?
2. how to stop memory leaks?
-->  “To prevent memory leaks, I make sure to clean up resources when components are destroyed. In Angular, that mainly means unsubscribing from RxJS observables using takeUntil or async pipe, removing event listeners, clearing timers, and avoiding unnecessary global references. I typically use ngOnDestroy() to handle cleanup.”
   eg.. use the sync pipe
   users$ = this.dataService.getUsers();
html-->
<div *ngFor="let user of users$ | async">
The async pipe:
Subscribes automatically
Triggers the API call
Updates UI with data
Unsubscribes on destroy

note- no need to subscribe in the ts 
   
4. tell me About angular life cycle hooks
5. when we redirected to one component to another then cal the ngOnInit()? or vs on click of back button called the ngOnInit?
6. in Rxjs what are you used?
7. What is new features in Angular 16/17?
8. which version you worked on and tell me feature about that version?
9. how to consume api --> write a code
10. where is first time getting data in api(service or in after subscriber)?
11. what is control flow?
12. explain the Rxjs methods?

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Revalsys technologies(feb 1/2026)
1. What is Angular ?
2. what is signals?
3. which version you worked on?
4. what is directives? explain about custome directives
5. what is SSR?
6. What is dynamic Routing?
7. how to manage meta tags dynamically in the Angular?
8. how to impact large image on project  performance?
9. What is hidreation?
10. what is microforntend?
11. What is lighthouse matrix?
12. how does works change detection in Angular?
13. What are the access neccsary to widows or document and what happen if used direct?
14. how to handle subscription to avoid memory leaks?
15. if you give the 4 projects then how you find the which project make in angular via browser?
Ans - by checking html have app-file name,ngContent,ngVersion,router-outlet property


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Infosys Interview(20 Jule 2026)
Role - Fullstack Developer

1. what you do in your current project

2. how to download and install angular what is required things and tell the steps
3. what is hoisting
4. what is dependency injection
5. slice vs plice
6. constructor vs ngOnInit
7. how to incarese the performance of the Angular Application
8. how we use pagination
9. guards
10. how works standalone component
11. what is lazy loading
12. if in api comes 400 and msg is whatever so how to handle this and check/400 → Bad Request
13. what is state management/why we use
14. what is action
15. what is ngrxjs
16. what is angular.json & package.json
17. what is diffrence between the map and filter map
18. what is lazy loading how we declare lazy loading
19. how we handle the large amount data in angular
20 css question-->
  where we use abstraction and relative position

21. what is oops
22. what is collection
23. difference between the list and set
24. how to crete any class which can access anyone
25. how to access data from database
26. features of java 8
27. how to handle exception in java
28. tell mi annotations in java
29. basic crud operation
30. how to connect with database
31. can we create the object of parent class in child class vs






