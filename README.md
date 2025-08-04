
# SWE Interview Prep Checklist

### ✅ 1. Fundamental Data Structures

#### Stacks & Queues
- [✅] **Stack:** Define the Last-In, First-Out (LIFO) principle.
- [✅] **Queue:** Define the First-In, First-Out (FIFO) principle.
- [✅] **Key Operations:** Understand push, pop, peek (for stacks) and enqueue, dequeue, peek (for queues).
- [✅] **Use Cases:** When would you choose one over the other?

> **My Explanation:**
**Stack operations**  
- `push(x)`: add **x** to the top of the stack  
- `pop()`: remove and return the top element (the most recently pushed)  
- `peek()`: return (but do not remove) the top element  
- `isEmpty()`: check whether the stack has no elements  

**Queue operations**  
- `enqueue(x)`: add **x** to the end (tail) of the queue  
- `dequeue()`: remove and return the front element (the earliest enqueued)  
- `peek()`: return (but do not remove) the front element  
- `isEmpty()`: check whether the queue has no elements 

**Use cases of Stack**
- **Browser History**
- when you click on a link, the visited page is added to the top of the stack, so when you want to go to the previous page visited you can just pop the currently visited page from the stack.
- going forwards and backwards requires two stacks, undostack and redo stack. 
- **DFS**
- start at the current node. push it into the stack and mark as seen. Then repeat the next steps until no elements in stack:
1) pop the next element in the stack
2) Process it (print it etc)
3) seeing if any of its neighbours are unseen, add it to the stack and mark them as seen.

**Use case of Queue**
- **CPU Scheduling**
- When a process is ready to access CPU resources, it gets queued to a scheduler, and the scheduler dequeues these processes to get a time slice of CPU, afterwhich it gets requeued (round robin). This ensures that processes don't get starved by newer processes requesting CPU time after an earlier process has asked for resources earlier. This guarantees no process will wait indefinately.
- **BFS**
- start at current node, mark it as seen, enqueue it. Then repeat following steps until queue is empty
1) dequeue next element from queue
2) visit the node
3) If any of the neighbors havent been seen/visited, enqueue them to the queue, and mark them as seen.

***When to use either***
1) If you need to do reversal or backtracking, use stack
2) if arrival order is important or ensuring breadthfirst fairness, use queues.

---

#### Arrays
- [ ] **Definition:** What is an array and how is it stored in memory? (contiguous memory block, fixed size, same data type).
- [ ] **Pros & Cons:** Fast O(1) access vs. slow O(n) insertion/deletion in the middle.
- [ ] **Operations:**
    - [ ] How to add elements (e.g., appending, inserting at an index).
    - [ ] How to remove elements (e.g., from the end, from an index).
- [ ] **Use Cases:** When is an array the right choice? (e.g., when you need frequent random access, storing data of a known size).

> **My Explanation:**
>
> *(Your notes here on array properties, performance, and common use cases...)*

---

### ✅ 2. Complex Data Structures

#### Binary Trees
- [ ] **Definition:** What is a binary tree? (A tree data structure where each node has at most two children).
- [ ] **Key Terminology:** Node, Root, Parent, Child, Leaf, Subtree.
- [ ] **Traversal Techniques:**
    - [ ] **In-Order Traversal:** (Left, Root, Right). What is its primary use case? (e.g., visiting nodes in non-decreasing order in a BST).
    - [ ] **Pre-Order Traversal:** (Root, Left, Right). What is its primary use case? (e.g., creating a copy of the tree).
    - [ ] **Post-Order Traversal:** (Left, Right, Root). What is its primary use case? (e.g., deleting nodes from a tree).

> **My Explanation:**
>
> *(Your notes here explaining each traversal method and why you'd use it...)*

---

#### Graphs
- [ ] **Definition:** What is a graph? (A collection of nodes/vertices connected by edges).
- [ ] **Key Terminology:** Vertex, Edge, Directed vs. Undirected, Weighted vs. Unweighted, Adjacency List/Matrix.
- [ ] **Traversal Algorithms:**
    - [ ] **Breadth-First Search (BFS):** How does it work? (Explores level by level). What data structure does it use? (**Queue**).
    - [ ] **Depth-First Search (DFS):** How does it work? (Explores as far as possible down one path before backtracking). What data structure does it use? (**Stack**, can be implemented recursively or iteratively).

> **My Explanation:**
>
> *(Your notes here on graph definitions and the step-by-step process of BFS and DFS...)*

---

### ✅ 3. Algorithms & Complexity

#### Searching Algorithms
- [ ] **Linear Search:** How does it work? What is its time complexity? (O(n)).
- [ ] **Binary Search:** How does it work? What is the key prerequisite for the data? (Must be sorted). What is its time complexity? (O(log n)).

> **My Explanation:**
>
> *(Your notes here on how each search algorithm functions and their performance characteristics...)*

---

#### Algorithmic Paradigms
- [ ] **Greedy Algorithms:**
    - [ ] **Concept:** Making the locally optimal choice at each step with the hope of finding a global optimum.
    - [ ] **Classic Problem:** Coin Change problem (for certain coin systems).
- [ ] **Dynamic Programming (DP):**
    - [ ] **Concept:** Breaking a problem down into smaller, overlapping subproblems and storing the results of these subproblems to avoid redundant calculations.
    - [ ] **Classic Problem:** Fibonacci sequence.

> **My Explanation:**
>
> *(Your notes here explaining the core idea behind Greedy vs. DP and how they apply to their classic problems...)*

---

#### Algorithmic Analysis
- [ ] **Time Complexity:** What does it measure? (How the runtime of an algorithm grows as the input size grows).
- [ ] **Space Complexity:** What does it measure? (How the amount of memory an algorithm uses grows as the input size grows).
- [ ] **Big O Notation:** Understand the common complexities:
    - [ ] O(1) - Constant
    - [ ] O(log n) - Logarithmic
    - [ ] O(n) - Linear
    - [ ] O(n log n) - Log-linear
    - [ ] O(n²) - Quadratic
    - [ ] O(2ⁿ) - Exponential
- [ ] **Time-Space Tradeoff:** Explain the concept of sacrificing memory usage to improve runtime, or vice versa.

> **My Explanation:**
>
> *(Your notes here defining Time/Space Complexity and the meaning of different Big O notations...)*

---

### ✅ 4. General Problem-Solving Approach

This is a meta-skill for how to approach any coding challenge in an interview.

- [ ] **1. Understand and Visualize:** Clarify any ambiguities in the problem statement. Draw the problem out, use example inputs/outputs.
- [ ] **2. Formulate a Brute-Force Solution:** Start with the most straightforward (even if inefficient) solution that works. This shows you can solve the problem.
- [ ] **3. Optimize:** Identify bottlenecks in the brute-force approach. Can you use a more efficient data structure? Can you apply a known algorithm or paradigm (Greedy, DP, etc.)? Discuss time-space tradeoffs.
- [ ] **4. Code:** Write clean, readable code.
- [ ] **5. Test and Debug:** Walk through your code with test cases, including edge cases. Use logging or print statements mentally (or literally) to trace execution.

> **My Explanation:**
>
> *(Your personal strategy for tackling a new problem from start to finish...)*

---

# Frontend & JavaScript Interview Prep Checklist

Use this checklist to track your study progress. For each concept, review the core ideas and then write your own summary in the "My Explanation" section to test your understanding.

### ✅ 1. Core JavaScript Concepts

#### Closures
- [ ] **Definition:** What is a closure? (A function that remembers the environment in which it was created, specifically its access to variables from its outer scope).
- [ ] **State Management:** How do closures enable private state? (e.g., the classic counter example).
- [ ] **Practical Examples:** Think of use cases like data privacy/encapsulation, or in callbacks where context is needed.

> **My Explanation:**
>
> *(Your notes here on what closures are and how they work...)*

---

#### Asynchronous JavaScript
- [ ] **Promises:**
    - [ ] **Concept:** What is a Promise? (An object representing the eventual completion or failure of an asynchronous operation).
    - [ ] **States:** Understand the three states: `pending`, `fulfilled`, `rejected`.
    - [ ] **Chaining:** How do `.then()` and `.catch()` work for handling success and error cases?
- [ ] **Async/Await:**
    - [ ] **Concept:** How does it provide "syntactic sugar" over Promises? (It makes async code look and behave more like synchronous code).
    - [ ] **`await` Keyword:** Explain how it pauses the execution of an `async` function until a Promise is settled.
    - [ ] **Error Handling:** How do you handle errors using `try...catch` blocks with `async/await`?

> **My Explanation:**
>
> *(Your notes here on Promises, async/await, and how they manage asynchronous operations...)*

---

### ✅ 2. The Document Object Model (DOM)

#### DOM Fundamentals
- [ ] **Definition:** What is the DOM? (A programming interface for web documents, representing the page so that programs can change the document structure, style, and content).
- [ ] **DOM Manipulation:** How do you select, create, add, and remove elements? (e.g., `querySelector`, `createElement`, `appendChild`, `remove`).
- [ ] **Virtual DOM:** What is it, and why do frameworks like React use it? (An in-memory representation of the real DOM; used to minimize direct DOM manipulations for performance).

> **My Explanation:**
>
> *(Your notes on the DOM, Virtual DOM, and basic manipulation...)*

---

#### Event Handling
- [ ] **Event Propagation:** Explain the two phases: **Capturing** (trickling down) and **Bubbling** (bubbling up).
- [ ] **Event Delegation:**
    - [ ] **Concept:** What is it? (Attaching a single event listener to a parent element to manage events for all of its children).
    - [ ] **Benefits:** Why is it more performant than attaching individual listeners? (Fewer listeners in memory, automatically handles dynamically added/removed child elements).
    - [ ] **Implementation:** How do you use the `event.target` property to identify which child triggered the event?

> **My Explanation:**
>
> *(Your notes here explaining event propagation and the event delegation pattern...)*

---

### ✅ 3. Web Development Concepts

#### Single-Page Applications (SPAs)
- [ ] **Concept:** What is an SPA? How does it differ from a traditional multi-page website? (Content is updated dynamically on the same page without a full reload).

#### Service Workers
- [ ] **Concept:** What is a Service Worker? (A script that the browser runs in the background, separate from a web page).
- [ ] **Use Cases:** What capabilities do they enable? (Offline access, push notifications, background sync, improved loading performance).

#### Browser Storage
- [ ] **Session Storage vs. Local Storage:** What is the key difference between them? (`sessionStorage` is cleared when the tab is closed; `localStorage` persists).

#### Responsive Design
- [ ] **Concept:** What does it mean for a site to be responsive?
- [ ] **Units:** Explain the difference and use cases for relative units like `%`, `rem`, `em`, `vw`, and `vh`.
- [ ] **Media Queries:** How are they used to apply different CSS rules based on device characteristics (like screen width)?

> **My Explanation:**
>
> *(Your notes on SPAs, Service Workers, Storage, and Responsive Design...)*

---

### ✅ 4. Performance Optimization

- [ ] **Minimizing DOM Manipulation:** Why is this important? Explain techniques like batching updates or manipulating elements "off-screen" before appending them.
- [ ] **Asset Optimization:**
    - [ ] How can you keep JS and CSS file sizes small? (Minification, removing unused code/libraries).
    - [ ] What is the role of a **CDN (Content Delivery Network)**?
    - [ ] What is **compression** (e.g., Gzip)?
- [ ] **Loading Strategies:**
    - [ ] **Lazy Loading:** What is it and when is it useful? (Loading resources like images only when they are needed/in the viewport).
    - [ ] **Code Splitting:** What is it? (Breaking your code into smaller chunks that can be loaded on demand).
    - [ ] **`async` vs. `defer`:** What is the difference when loading scripts?
- [ ] **Event Handling:**
    - [ ] **Throttling & Debouncing:** Explain the difference and when you would use each. (Useful for frequent events like scroll or resize).

> **My Explanation:**
>
> *(Your notes detailing various web performance techniques...)*

---

### ✅ 5. Development Best Practices

#### Semantic HTML
- [ ] **Concept:** What is Semantic HTML? (Using HTML tags that accurately describe the meaning and structure of the content).
- [ ] **Benefits:** Why is it important? (Improves **SEO** for search engine ranking and **Accessibility** for screen readers).
- [ ] **Examples:** Be able to name and explain tags like `<article>`, `<section>`, `<nav>`, and `<aside>`.

#### Accessibility (A11y)
- [ ] **Core Principles (WCAG):** What are the key areas of web accessibility?
    - [ ] **Keyboard Accessibility:** Ensuring all functionality is usable with a keyboard alone.
    - [ ] **Screen Reader Support:** Using **Semantic HTML**, proper labels for forms, and **ARIA** attributes.
    - [ ] **Visuals:** Maintaining good **color contrast** and providing visible **focus indicators**.

#### Cross-Browser Compatibility
- [ ] **Concept:** What challenges arise from different browsers interpreting code differently?
- [ ] **Tooling:**
    - [ ] What is **Babel** used for? (Transpiling modern JavaScript into older, more compatible versions).
    - [ ] What are **Polyfills**? (Code that provides modern functionality on older browsers that don't support it natively).

#### Debugging
- [ ] **Techniques:** How do you debug JavaScript in the browser?
    - [ ] **Browser DevTools:** Using the Console, Sources panel, Network tab, etc.
    - [ ] **`console.log()`:** The simplest method for tracing values.
    - [ ] **`debugger` statement:** How does it work to pause execution?

> **My Explanation:**
>
> *(Your notes on writing semantic, accessible, compatible, and debuggable code...)*

---

### ✅ 6. Testing

#### Manual Testing
- [ ] **Process:** Outline a simple manual testing strategy for a web page.
    - [ ] **Functional Testing:** Does everything work as expected (buttons, forms, links)?
    - [ ] **Responsive Testing:** Does the layout look correct on different screen sizes (desktop, tablet, mobile)?
    - [ ] **Cross-Browser Testing:** Does it work correctly in major browsers (Chrome, Firefox, Safari)?
    - [ ] **Accessibility Check:** Can you navigate with a keyboard? Do images have alt text?

> **My Explanation:**
>
> *(Your personal checklist for manually testing a feature or page...)*


---

- explain restful api
 - get post put and delete
 - how they interact with web resources

 - what is stateless communication (client has all data, no stored context on server)

 - status codes? meaningful feedback, error handling and debugging

 what makes rest api easier, simplcity in mind, use standard protocol like http, applications regardless of device since its standardized. consistent protocol easier for maitenence and integration for scalability

 - how versioning, management of states, restful f


 - do restful use json (lightweight easy to parse) or xml

 - scalability how in restful, so the statelessness and uniform. dedicated routes, more scalable systems. 

 decoupled services, independently as needed, servers (load balancer) withou tneeding to change api.  