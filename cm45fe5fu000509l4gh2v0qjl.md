---
title: "Introduction to Scope & Closure: JavaScript"
datePublished: Sun Dec 01 2024 09:55:24 GMT+0000 (Coordinated Universal Time)
cuid: cm45fe5fu000509l4gh2v0qjl
slug: introduction-to-scope-closure-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733046846534/e4a1a933-afa7-41dc-998d-898674f0bef3.jpeg
tags: javascript, scope-in-js, closures-in-javascript

---

### স্কোপ

স্কোপ হল ভ্যারিয়েবল এবং ফাংশন কোথা থেকে অ্যাক্সেস করা যাবে তার নিয়ম। জাভাস্ক্রিপ্টে মূলত দুটি ধরণের স্কোপ রয়েছে:

1. **গ্লোবাল স্কোপ:** যখন একটি ভ্যারিয়েবল বা ফাংশন পুরো প্রোগ্রামে যেকোনো স্থান থেকে অ্যাক্সেস করা যায়, তখন সেটি গ্লোবাল স্কোপের অন্তর্ভুক্ত। গ্লোবাল স্কোপে তৈরি ভ্যারিয়েবলগুলি মেমোরিতে অনেক সময় ধরে থাকে।
    
    ```jsx
    var globalVariable = "আমি গ্লোবাল স্কোপে আছি";
    
    function showGlobal() {
        console.log(globalVariable);
    }
    
    showGlobal();
    
    ```
    
2. **লোকাল স্কোপ:** এই স্কোপে ফাংশনের ভেতরে ডিক্লেয়ার করা ভ্যারিয়েবল শুধুমাত্র সেই ফাংশনের মধ্যেই অ্যাক্সেস করা যায়। একে ফাংশন স্কোপও বলা হয়।
    
    ```jsx
    function localScopeExample() {
        var msg = "আমি লোকাল স্কোপে আছি";
        console.log(msg);
    }
    
    localScopeExample();
    console.log(msg); // এরর আসবে কারণ a ভেরিয়েবলটি গ্লোবাল স্কোপে নাই।
    
    ```
    

### ব্লক স্কোপ

ES6 ভার্সনে আমরা `let` এবং `const` এর সাথে পরিচিত হয়। `var` এর সাথে এগুলোর পার্থক্য হলো এগুলো {} ব্লকের মধ্যে ভ্যারিয়েবল সীমাবদ্ধ রাখে, যেখানে `var` {} ব্লকের বাইরেও এক্সেসযোগ্য।

```jsx
{
    let blockScoped = "আমি ব্লক স্কোপে আছি";
    console.log(blockScoped); // ঠিকঠাক কাজ করবে
}

console.log(blockScoped); // এরর আসবে কারণ এটি ব্লকের বাইরে।

```

### ক্লোজার

ক্লোজার হল এমন একটি ফাংশন যা তার চারপাশের স্কোপ থেকে ডেটা অ্যাক্সেস করতে পারে, এমনকি সেই স্কোপের বাইরেও। এটি মূলত ফাংশনের সাথে সাথে তার স্কোপকেও মনে রাখে। এটা এমন একটি ফাংশন যার প্যারেন্ট ফাংশন কাজ করা বন্ধ করে দিলেও এই ফাংশনটি প্যারেন্টের স্কোপকে এক্সেস করতে পারে।

```jsx
function outerFunction() {
    let outerVariable = "আমি ভ্যারিয়েবল";

    function innerFunction() {
        console.log(outerVariable);
    }

    return innerFunction;
}

const myClosure = outerFunction();
myClosure(); // "আমি ভ্যারিয়েবল" আউটপুট হবে।

```

ক্লোজারের ব্যবহার ক্ষেত্র:

* ডেটা প্রাইভেট রাখা।
    
* ফাংশনের ভেতর ফাংশন তৈরি করা।
    
* কারিং (Currying) ফাংশন ইমপ্লিমেন্ট করা।
    

### স্কোপ এবং ক্লোজারের উদাহরণ

1. **ডেটা প্রাইভেট রাখা:**
    
    ```jsx
    function createCounter() {
        let count = 0;
    
        return function() {
            count++;
            return count;
        };
    }
    
    const counter = createCounter();
    console.log(counter()); // 1
    console.log(counter()); // 2
    
    ```
    
2. **কারিং (Currying) ফাংশন:**
    
    ```jsx
    function multiplier(factor) {
        return function(number) {
            return number * factor;
        };
    }
    
    const double = multiplier(2);
    console.log(double(5)); // 10
    
    const triple = multiplier(3);
    console.log(triple(5)); // 15
    
    ```
    
    এখানে ক্লোজারের কারণেই সম্ভব হয়েছে factor ভেরিয়েবলকে মনে রাখার!
    

Content Writing: **Mohammad Sefatullah**

**#scope** **#closure** **#mukticoders** **#variables** **#function** **#javascript**