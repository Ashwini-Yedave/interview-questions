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
