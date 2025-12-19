## A. Beginner Explanation (প্রাথমিক ব্যাখ্যা)

**Pure Function** হলো এমন একটি ফাংশন, যা গণিতের ফাংশনগুলোর মতো কাজ করে। একটি ফাংশন "Pure" বা **বিশুদ্ধ** হবে যদি এটি নিম্নলিখিত দুটি শর্ত পূরণ করে:

১. **একই ইনপুট → একই আউটপুট (Deterministic):** আপনি যদি একই আর্গুমেন্ট (ইনপুট) দিয়ে ফাংশনটিকে বারবার কল করেন, তবে এটি সর্বদা **একই আউটপুট** দেবে। এটি সময়, ডেটাবেসের অবস্থা বা নেটওয়ার্ক কলের উপর নির্ভর করে না।

২. **কোনো পার্শ্ব-প্রতিক্রিয়া নেই (No Side Effects):** ফাংশনটি তার নিজস্ব স্কোপের বাইরে কোনো কিছুকে **পরিবর্তন** করতে পারে না। উদাহরণস্বরূপ: * গ্লোবাল ভেরিয়েবল পরিবর্তন করা। * কনসোল বা স্ক্রিনে কিছু প্রিন্ট করা। * একটি ডেটাবেসে লেখা বা নেটওয়ার্ক কল করা। * আর্গুমেন্ট হিসেবে প্রাপ্ত কোনো অবজেক্ট বা অ্যারে পরিবর্তন করা।

সহজ কথায়, একটি Pure Function হলো একটি **"Calculator"**। এটি শুধু ইনপুট নেয়, গণনা করে এবং আউটপুট দেয়। এটি বাইরের বিশ্বকে স্পর্শ করে না।

---
## B. Intermediate Details (মধ্যবর্তী বিবরণ)

Pure Function-এর মূল উদ্দেশ্য হলো **Predictability (পূর্বাভাসযোগ্যতা)** এবং **Testability (পরীক্ষাযোগ্যতা)**।

- **Referential Transparency (রেফারেনশিয়াল স্বচ্ছতা):** একটি Pure Function-এর ফলাফল সর্বদা এর কলের সাথে প্রতিস্থাপন করা যেতে পারে, কোনো প্রোগ্রামের আচরণ পরিবর্তন না করে। অর্থাৎ, f(x) কে সরাসরি y (যেখানে y=f(x)) দিয়ে প্রতিস্থাপন করা যায়। এটি কম্পাইলারকে **Optimization (অপটিমাইজেশন)** করার সুবিধা দেয়।
    
- **Immutability (অপরিবর্তনীয়তা):** Pure Function প্রায়শই **Immutable Data Structures** ব্যবহার করে, যার ফলে ফাংশনটি প্যারামিটার বা বাইরের কোনো স্টেটকে পরিবর্তন না করে নতুন ডেটা রিটার্ন করে। JavaScript-এ Primitive Data Types (String, Number) স্বভাবতই Immutable, কিন্তু Objects ও Arrays পরিবর্তনশীল (Mutable)। তাই এই ক্ষেত্রে Pure Functions তৈরি করার সময় সতর্কতা অবলম্বন করতে হয়।
    
- **Concurrency:** যেহেতু Pure Functions কোনো শেয়ার্ড স্টেট পরিবর্তন করে না, তাই এগুলোকে Parallel (সমান্তরালভাবে) এবং Concurrent (একযোগে) চালানো নিরাপদ।
    
---
## C. Advanced Analysis (উচ্চতর বিশ্লেষণ)

### Low-Level / Internals

Pure Function-এর ক্ষেত্রে, যখন ফাংশনটি কল করা হয়, তখন এটি তার নিজস্ব **Execution Context** তৈরি করে, যার মধ্যে শুধুমাত্র তার লোকাল ভেরিয়েবল এবং আর্গুমেন্ট থাকে। বাইরে থেকে আসা কোনো ডেটা (আর্গুমেন্ট ছাড়া) এটি স্পর্শ করে না।
### Memory & Life Cycle

Pure Function-এর জীবনচক্র খুবই সরল। ১. **Allocation:** ফাংশনটি কল হলে স্ট্যাক (Stack) এ তার লোকাল ভেরিয়েবলগুলোর জন্য মেমরি বরাদ্দ হয়। ২. **Execution:** এটি তার গণনা সম্পন্ন করে। ৩. **Return & Deallocation:** আউটপুট রিটার্ন করার পর, এর লোকাল মেমরি স্ট্যাক থেকে **Deallocate** হয়ে যায়। গুরুত্বপূর্ণ দিক: Pure Functions ডেটা পরিবর্তন না করে নতুন ডেটা তৈরি করে, ফলে **Garbage Collector** কে পুরনো ডেটা পরিষ্কার করার জন্য বেশি কাজ করতে হয়। কিন্তু এর সুবিধা হলো মেমরি লিকেজ (Memory Leakage) এবং অনাকাঙ্ক্ষিত সাইড ইফেক্টের ঝুঁকি কমে যায়।

### Memoization

যেহেতু Pure Functions Deterministic, তাই একই ইনপুটের জন্য আউটপুট ক্যাশ করা যেতে পারে। এই কৌশলকে **Memoization** বলে। বারবার একই গণনা না করে ক্যাশড ফলাফল ব্যবহার করলে প্রোগ্রামের পারফরম্যান্স বহুগুণ বেড়ে যায়।

---
## D. Full Breakdown (Numbered)

একটি ফাংশন কিভাবে Pure হবে, তার বিশ্লেষণ:

১. **ইনপুট গ্রহণ (Input):** ফাংশনটি এক বা একাধিক আর্গুমেন্ট প্যারামিটার হিসেবে গ্রহণ করবে। ২. **শুধুমাত্র গণনা (Calculation Only):** ফাংশনের বডির মধ্যে থাকা সমস্ত অপারেশন অবশ্যই আর্গুমেন্টের উপর ভিত্তি করে হবে। এখানে `Date.now()`, `Math.random()`, বা কোনো গ্লোবাল ভেরিয়েবল ব্যবহার করা যাবে না। ৩. **গ্লোবাল অ্যাক্সেস (No Global Access/Mutation):** ফাংশনটি তার নিজস্ব স্কোপের বাইরে সংজ্ঞায়িত কোনো ভেরিয়েবল বা অবজেক্টের মান **পড়বে না বা লিখবে না** (closure থেকে read করা যেতে পারে, কিন্তু mutate করা যাবে না)। ৪. **সাইড ইফেক্ট বর্জন (Avoid Side Effects):** ফাংশনের মধ্যে `console.log()`, `document.getElementById()`, ডেটাবেস/ফাইল অপারেশন, বা কোনো I/O অপারেশন থাকা যাবে না। ৫. **নতুন আউটপুট প্রদান (Return New Output):** যদি ইনপুট অবজেক্ট বা অ্যারে হয়, তবে ফাংশনটি সেগুলোকে পরিবর্তন না করে (Immutability বজায় রেখে) **নতুন** একটি অবজেক্ট বা অ্যারে রিটার্ন করবে। ৬. **আউটপুট প্রদান (Output):** ফাংশনটি গণনা শেষে অবশ্যই একটি মান রিটার্ন করবে।

---
## E. Code Examples (কোড উদাহরণ)

### ১. Basic (Pure)

এই ফাংশনটি শুধু ইনপুট আর্গুমেন্টের উপর নির্ভর করে। এটি কোনো সাইড ইফেক্ট তৈরি করে না।

```js
/**
 * দুটি সংখ্যা যোগ করে নতুন সংখ্যা রিটার্ন করে।
 * @param {number} a
 * @param {number} b
 * @returns {number}
 */
const add = (a, b) => {
  return a + b;
};

// Expected Output:
// add(5, 3) → 8
// add(5, 3) → 8 (বারবার কল করলেও একই)
```

### ২. Wrong (Impure)

এই ফাংশনটি গ্লোবাল ভেরিয়েবল পরিবর্তন করছে এবং ইনপুট অবজেক্টকে পরিবর্তন করছে।

```js
let globalCounter = 0; // Global State
const initialData = { value: 10 }; // Mutable Input

/**
 * ইনপুট অবজেক্ট পরিবর্তন করে এবং গ্লোবাল কাউন্টার বাড়ায়।
 * এটি Impure কারণ: Side-effect (globalCounter পরিবর্তন) এবং Mutation (obj পরিবর্তন)।
 * @param {object} obj
 * @returns {object}
 */
const impureFunction = (obj) => {
  globalCounter += 1; // Side Effect: Global Variable Mutation
  obj.value += 1;     // Side Effect: Input Argument Mutation
  console.log("Global counter updated"); // Side Effect: I/O (console)
  return obj;
};

// Test Case:
// const result1 = impureFunction(initialData); // { value: 11 }, globalCounter: 1
// const result2 = impureFunction(initialData); // { value: 12 }, globalCounter: 2
// **একই ইনপুট (initialData) দ্বিতীয়বার ভিন্ন আউটপুট দিল, কারণ এটি প্রথমবার পরিবর্তন হয়েছে।**
```

### ৩. Fixed (Pure)

এই ফাংশনটি গ্লোবাল স্টেট ব্যবহার করে না এবং ইনপুট অবজেক্টকে পরিবর্তন না করে নতুন অবজেক্ট তৈরি করে।

```js
const globalCounter = 0; // Fixed: Global variable used only as reference (not mutated)
const initialData = { value: 10 };

/**
 * ইনপুট অবজেক্টকে পরিবর্তন না করে নতুন অবজেক্ট তৈরি করে।
 * Pure: কোনো Side-effect নেই, কোনো Mutation নেই।
 * @param {object} obj
 * @returns {object}
 */
const pureFunctionFixed = (obj) => {
  const newValue = obj.value + 1;
  // obj.value = newValue; // এড়িয়ে যাওয়া হলো
  return { ...obj, value: newValue }; // Immutability: নতুন অবজেক্ট রিটার্ন করা হলো
};

// Test Case:
// const result1 = pureFunctionFixed(initialData); // initialData: { value: 10 }, result1: { value: 11 }
// const result2 = pureFunctionFixed(initialData); // initialData: { value: 10 }, result2: { value: 11 }
// **একই ইনপুট (initialData) দ্বিতীয়বার একই আউটপুট দিল, কারণ initialData অপরিবর্তিত আছে।**
```

___
## F. Line-by-line Comments

উপরে প্রদত্ত `pureFunctionFixed` উদাহরণটির লাইন-বাই-লাইন বিশ্লেষণ:

```js
const pureFunctionFixed = (obj) => {            // ফাংশনটি `obj` নামক একটি অবজেক্ট প্যারামিটার হিসেবে গ্রহণ করছে।
  const newValue = obj.value + 1;               // আর্গুমেন্টের মান ব্যবহার করে লোকাল স্কোপে একটি নতুন মান গণনা করা হচ্ছে।
  return { ...obj, value: newValue };           // Spread Operator (...) ব্যবহার করে ইনপুট অবজেক্টকে কপি করা হচ্ছে।
};                                              // তারপর কেবল 'value' প্রপার্টিটিকে নতুন মান দিয়ে ওভাররাইড করে **একটি নতুন অবজেক্ট** রিটার্ন করা হচ্ছে।
```

___
## G. Performance & Complexity

|মেট্রিক|বিবরণ|
|---|---|
|**Big-O**|Pure Functions-এর Big-O নির্ভর করে এর ভেতরের অপারেশনের উপর। উদাহরণস্বরূপ, দুটি সংখ্যা যোগ করা হলো O(1)।|
|**Bottlenecks**|**Immutability-এর কারণে সৃষ্ট ওভারহেড (Overhead)** একটি প্রধান Bottleneck হতে পারে। বড় অ্যারে বা অবজেক্টের ক্ষেত্রে প্রতিটি কলে কপি তৈরি করতে বেশি CPU এবং মেমরি খরচ হয়।|
|**Memory Notes**|Pure Functions মেমরি মুক্তিতে সহায়ক, কিন্তু নতুন ডেটা তৈরির কারণে অস্থায়ীভাবে **অতিরিক্ত মেমরি** ব্যবহার করতে পারে, যা পরে Garbage Collector দ্বারা পরিষ্কার করা হয়।|
|**Optimization**|**Memoization** বা ক্যাশিং ব্যবহার করে Pure Functions-এর পারফরম্যান্স উল্লেখযোগ্যভাবে বাড়ানো যায়, যা Impure Functions-এ সম্ভব নয়।|
___
## H. Security & Edge Cases

|ক্ষেত্র|বিবরণ|
|---|---|
|**ইনপুট ভ্যালিডেশন**|Pure Functions-এও ইনপুট ভ্যালিডেশন জরুরি। যদি `add(5, "hello")` কল করা হয়, তবে অপ্রত্যাশিত আচরণ ঘটতে পারে। তাই Type Checking (যেমন TypeScript বা JSDoc) ব্যবহার করা আবশ্যক।|
|**Race Condition**|Pure Functions কোনো শেয়ার্ড স্টেট পরিবর্তন করে না, তাই **Race Condition** ঘটার কোনো সম্ভাবনা নেই। এটি Concurrency-এর ক্ষেত্রে একটি বিশাল নিরাপত্তা সুবিধা।|
|**Pitfalls (ফাঁদ)**|Mutable অবজেক্টকে ইনপুট হিসেবে নিয়ে যদি ফাংশনের ভেতরে পরিবর্তন করা হয়, তবে ফাংশনটি দৃশ্যত Pure মনে হলেও, এটি আসলে **Impure** হবে (যেমন `Array.prototype.push()` ব্যবহার করা)।|
|**Error Handling**|Pure Functions-এ সাধারণত Errors (যেমন Division by Zero) রিটার্ন মানের মাধ্যমে পরিচালনা করা উচিত, I/O-তে না লিখে।|
___
## I. Cross-language Comparison

|বৈশিষ্ট্য|JavaScript (JS)|Python|Java|C++|
|---|---|---|---|---|
|**Core Concept**|Functional Programming (FP) এর ভিত্তি। React/Redux-এ ব্যবহৃত।|FP সমর্থিত (Lambda, `map`, `filter`)। ভ্যারিয়েবল স্বভাবতই লোকাল।|FP-কে Java 8+ এ Lambda/Stream API দিয়ে যুক্ত করা হয়েছে।|OOP-তে জোর বেশি। ফাংশনাল ব্যবহার সম্ভব (Templates, Lambdas)।|
|**Mutation Risk**|Object/Array Mutation-এর ঝুঁকি বেশি। স্প্রেড অপারেটর (`...`) বা Immutable.js লাগে।|Lists/Dicts Mutable, তাই কপি করা (e.g., `list[:]`) জরুরি।|Primitive Immutable. Objects (e.g., `ArrayList`) Mutable।|C++ এ `const` কিওয়ার্ড ব্যবহার করে ইনপুটকে অপরিবর্তনীয় করা হয়।|
|**Example Utility**|স্টেট ম্যানেজমেন্ট, Array Transformation।|Data Processing, Mathematical Functions।|Stream Pipelining, Concurrency।|Complex Algorithms, High-Performance Math।|
___
## J. ASCII Visuals (ফ্লোচার্ট)

Pure Function-এর ইনপুট-আউটপুট ফ্লো এবং Side-Effect-এর অনুপস্থিতি নির্দেশক ডায়াগ্রাম:

```
graph LR
    subgraph External State (Global Variables, DB, Console)
        A[External/Shared Data]
    end

    subgraph Pure Function Call Stack
        B(Input: Arguments x, y) --> C{Operation: x + y}
        C --> D(Output: Result z)
    end

    A --- No Direct Connection ---> C
    D --- No Direct Connection ---> A

    style External State fill:#fdd,stroke:#333
    style Pure Function Call Stack fill:#dff,stroke:#333
    style A fill:#fdd,stroke:#c33
    style D fill:#ddf,stroke:#33c
    
    A & D  --- Only via Function Signature --->  B
```

___
## K. Best Practices (৬টি প্রোডাকশন-গ্রেড টিপস)

১. **প্যারামিটার ইমিউটেবিলিটি (Parameter Immutability):** ফাংশনের ভেতরে কখনোই প্যারামিটার অবজেক্ট বা অ্যারে পরিবর্তন করবেন না। অবজেক্টের ক্ষেত্রে স্প্রেড অপারেটর (`...`) বা `Object.assign()` ব্যবহার করে কপি তৈরি করুন। ২. **ছোট এবং একক উদ্দেশ্য (Small & Single Purpose):** প্রতিটি Pure Function একটি মাত্র কাজ করবে। এটি ফাংশন কম্পোজিশন (Function Composition) সহজ করে। ৩. **Side Effect Separation:** যদি আপনার Side Effect (যেমন logging, network call) লাগেই, তবে সেগুলোকে Pure Functions থেকে **আলাদা Impure Wrapper Function** এ রাখুন। ৪. **Currying/Composition:** Pure Functions সহজেই Currying বা ফাংশন কম্পোজিশন-এর জন্য ব্যবহার করা যায়, যা রিডেবিলিটি ও মডুলারিটি বাড়ায়। ৫. **Strict Type Checking:** TypeScript ব্যবহার করুন বা JSDoc দিয়ে ইনপুট/আউটপুটের প্রকারভেদ স্পষ্টভাবে সংজ্ঞায়িত করুন, যাতে অপ্রত্যাশিত ইনপুট এড়ানো যায়। ৬. **Deterministic External Data:** যদি কোনো Pure Function-এ ডেটাবেস থেকে ডেটা আনতে হয়, তবে সেই ডেটা আনার প্রক্রিয়াটি অবশ্যই ফাংশনের বাইরে থাকতে হবে। Pure Function কেবল সেই ডেটা নিয়ে গণনা করবে।

___
## L. Anti-patterns (৬টি বর্জনীয় ব্যবহার)

১. **Mutable ডেটা ইনপুট:** Mutable অবজেক্ট ইনপুট নিয়ে যদি আপনি কপি তৈরি করতে ভুলে যান, তবে এটি একটি Anti-pattern। ২. **Random/Date নির্ভরশীলতা:** `Math.random()` বা `Date.now()` ব্যবহার করা উচিত নয়, কারণ এটি Deterministic শর্ত ভঙ্গ করে। ৩. **I/O সরাসরি ফাংশনে:** `fetch()`, `console.log()`, `localStorage` ব্যবহার করা উচিত নয়। ৪. **Closure Mutation:** ফাংশনটি Pure হলেও যদি এর ভেতরের একটি Closure বাইরের স্কোপের ভেরিয়েবলকে পরিবর্তন করে, তবে তা Impure হবে। ৫. **আর্গুমেন্ট রিমুভাল:** যদি ফাংশনটি কোনো আর্গুমেন্টকে **ডিলিট** করে (যেমন `delete obj.prop`), তবে এটি একটি Mutation এবং Anti-pattern। ৬. **Too Much Copying:** খুব বড় ডেটা স্ট্রাকচারে সামান্য পরিবর্তনের জন্য প্রতিবার সম্পূর্ণ কপি তৈরি করা (Deep Copy) পারফরম্যান্সের জন্য ক্ষতিকারক হতে পারে। এই ক্ষেত্রে সাবধানে ইমিউটেবল লাইব্রেরি ব্যবহার করা ভালো।

---
## M. FAQ (৫টি প্রশ্ন)

**১. কেন আমার Pure Function ব্যবহার করা উচিত?**

- **উত্তর:** এটি কোডকে পূর্বাভাসযোগ্য (Predictable) করে, ডিবাগ করা সহজ হয় এবং ইউনিট টেস্টিং দ্রুত ও নির্ভরযোগ্য হয়।
    
**২. সকল ফাংশন কি Pure হতে পারে?**

- **উত্তর:** না। I/O অপারেশন (ডেটাবেস, নেটওয়ার্ক, ইউজার ইন্টারফেস পরিবর্তন) সব সময় Impure ফাংশনের মাধ্যমে করতে হয়। Pure Functions হলো ব্যবসার যুক্তির (Business Logic) জন্য।
    
**৩. Pure Function-এ কি `console.log()` ব্যবহার করা যায়?**

- **উত্তর:** টেকনিক্যালি, `console.log()` একটি **Side Effect**, তাই একটি কঠোরভাবে Pure Function-এ এটি ব্যবহার করা উচিত নয়। ডিবাগিং-এর জন্য ব্যবহার করা যেতে পারে, তবে প্রোডাকশন কোডে এর ব্যবহার ফাংশনটিকে Impure করে তোলে।
    
**৪. `map()` বা `filter()` কি Pure?**

- **উত্তর:** হ্যাঁ। JavaScript-এর বিল্ট-ইন অ্যারে মেথড যেমন `map()`, `filter()`, এবং `reduce()` Pure, কারণ তারা বিদ্যমান অ্যারে পরিবর্তন না করে **নতুন অ্যারে** রিটার্ন করে।
    
**৫. কিভাবে একটি Impure ফাংশনকে Pure করা যায়?**

- **উত্তর:** Impure ফাংশন থেকে Side Effect (যেমন গ্লোবাল ভেরিয়েবল অ্যাক্সেস, I/O) সরিয়ে দিন এবং সব প্রয়োজনীয় ডেটা প্যারামিটার হিসেবে গ্রহণ করুন। ইনপুট ডেটা পরিবর্তন না করে নতুন ডেটা রিটার্ন করুন।
    
---
## N. Exercises (অনুশীলন)

### ১. Easy: Array Sum (Pure Function তৈরি)

একটি অ্যারের উপাদানগুলোর যোগফল নির্ণয়ের জন্য একটি Pure Function লিখুন।

```js
/* Exercise 1 */
const calculateSum = (numbers) => {
  // আপনার কোড এখানে
  return numbers.reduce((acc, current) => acc + current, 0);
};

// Expected Output:
// calculateSum([10, 20, 30]) → 60
// calculateSum([5, 5]) → 10
```

### ২. Medium: Object Update (Immutability সহ)

একটি ইউজার অবজেক্ট এবং একটি নতুন বয়স নিয়ে একটি Pure Function লিখুন, যা ইউজার অবজেক্টের `age` প্রপার্টি পরিবর্তন না করে একটি **নতুন** ইউজার অবজেক্ট রিটার্ন করবে।

```js
/* Exercise 2 */
const updateAgePurely = (user, newAge) => {
  // আপনার কোড এখানে
  return { ...user, age: newAge };
};

// Test Case:
const initialUser = { name: "Alice", age: 25 };
const newUser = updateAgePurely(initialUser, 26);

// Expected Output:
// newUser → { name: "Alice", age: 26 }
// initialUser → { name: "Alice", age: 25 } (Unchanged)
```

### ৩. Hard: Inconsistent Filter (Impure কোডকে Pure করা)

নিচের Impure ফাংশনটিকে Pure করুন, যাতে এটি গ্লোবাল অ্যারে পরিবর্তন না করে।

```js
/* Exercise 3 (Impure to Pure) */
let globalCart = [100, 50, 200, 30]; // গ্লোবাল অ্যারে

const filterAndMutateImpure = (minPrice) => {
  // Impure: এই গ্লোবাল ভেরিয়েবলটি পরিবর্তিত হচ্ছে!
  globalCart = globalCart.filter(price => price >= minPrice);
  return globalCart;
};

// Test Case (Impure):
// const result1 = filterAndMutateImpure(100); // globalCart: [100, 200]
// const result2 = filterAndMutateImpure(150); // globalCart: [200] (ভিন্ন আউটপুট কারণ state পরিবর্তিত)

// Pure Solution:
const filterPurely = (cart, minPrice) => {
  // আপনার কোড এখানে
  return cart.filter(price => price >= minPrice); // নতুন অ্যারে রিটার্ন
};

// Expected Output (Pure):
// const cart = [100, 50, 200, 30];
// filterPurely(cart, 100) → [100, 200]
// filterPurely(cart, 150) → [200]
// cart → [100, 50, 200, 30] (Original cart remains unchanged)
```

___
## O. References (৩টি বই/ডকুমেন্টের নাম)

১. **Composing Software: An Introduction to Functional Programming and Reactive Programming** (বই) ২. **Professor Frisby's Mostly Adequate Guide to Functional Programming** (অনলাইন বুক) ৩. **Functional JavaScript** (বই)

---
## 6. REAL-WORLD Case Study (বাস্তব ক্ষেত্রে ব্যবহার)

### কেস স্টাডি ১: React State Management (Redux/Zustand)

- **সমস্যা:** বড় মাপের Web Application-এ State (অ্যাপ্লিকেশন ডেটা)-এর পরিবর্তন ট্র‍্যাক করা কঠিন হয়ে ওঠে, কারণ বিভিন্ন কম্পোনেন্ট একই ডেটা পরিবর্তন করতে পারে। এতে Race Condition এবং অনাকাঙ্ক্ষিত বাগ দেখা দেয়।
    
- **Pure Function সমাধান:** **Redux** বা **Zustand** এর মতো স্টেট ম্যানেজমেন্ট লাইব্রেরিগুলো স্টেট পরিবর্তন করার জন্য **Reducers** ব্যবহার করে। Reducer হলো কঠোরভাবে Pure Function।
    
    - **ইনপুট:** বর্তমান স্টেট (Current State) এবং অ্যাকশন অবজেক্ট (Action Object)।
        
    - **কাজ:** এই Reducers-গুলো বর্তমান স্টেট অবজেক্টকে **কখনোই পরিবর্তন করে না** (No Mutation)। তারা সবসময় একটি নতুন স্টেট অবজেক্ট তৈরি করে রিটার্ন করে।
        
    - **ফলাফল:** এই ইমিউটেবিলিটি (Immutability) নিশ্চিত করে যে স্টেটের পরিবর্তন সব সময় Predictable এবং একটি নির্দিষ্ট অ্যাকশনের ফলাফল সর্বদা একই হবে (Referential Transparency)।
        
### কেস স্টাডি ২: Data Transformation Pipelining

- **সমস্যা:** ডেটা প্রসেসিং অ্যাপ্লিকেশনগুলোতে (যেমন ETL বা ডেটা বিশ্লেষণ) ডেটাকে ধাপে ধাপে রূপান্তর (Transformation) করতে হয়। যদি একটি ধাপ ভুল করে ইনপুট ডেটাকে পরিবর্তন করে ফেলে, তবে পরের ধাপের ফলাফল ভুল হবে এবং ডিবাগ করা কঠিন হবে।
    
- **Pure Function সমাধান:** ইঞ্জিনিয়াররা ডেটা প্রসেসিং-এর জন্য **Functional Pipelining** ব্যবহার করেন।
    
    - **ধাপ:** প্রতিটি প্রসেসিং ধাপ (যেমন, ডেটা ফিল্টারিং, সর্টিং, ক্যালকুলেশন) একটি Pure Function হিসেবে লেখা হয়।
        
    - **ফ্লো:** প্রথম Pure Function-এর আউটপুট দ্বিতীয়টির ইনপুট হয়, এবং এভাবে চলতে থাকে।
        
    - **ফলাফল:** যেহেতু প্রতিটি ফাংশন ইনপুট ডেটা পরিবর্তন করে না, তাই ডেটার অখণ্ডতা (Integrity) বজায় থাকে। প্রতিটি ধাপের আউটপুট স্বাধীনভাবে টেস্ট করা যায় এবং পুরো পাইপলাইনের ডিবাগিং অত্যন্ত সহজ হয়ে যায়।