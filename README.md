
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
- [✅] **Definition:** What is an array and how is it stored in memory? (contiguous memory block, fixed size, same data type).
- [✅] **Pros & Cons:** Fast O(1) access vs. slow O(n) insertion/deletion in the middle.
- [✅] **Operations:**
    - [✅] How to add elements (e.g., appending, inserting at an index).
    - [✅] How to remove elements (e.g., from the end, from an index).
- [✅] **Use Cases:** When is an array the right choice? (e.g., when you need frequent random access, storing data of a known size).

> **My Explanation:**
### Arrays

An array is a collection of items of the same type stored in memory. 
- They are stored contiguously
- The size of the array is fixed when its created.
- Each item has a unique index.
- if you know base address and size of each item, you can access any part of the array.

To access the element at index `i`, the formula is:
`Address(element[i]) = Base Address + (i * size_of_each_element)`

For `element[3]`: `1000 + (3 * 4) = 1000 + 12 = 1012`. This direct calculation is why access is so fast.

*   **Pros:**
    *   **Fast O(1) Access (Constant Time):** This is the biggest advantage. 
    - Items stored contiguously, you can access any element directly by its index in constant time, regardless of the array's size. Y
    - You don't need to traverse the array. This is often referred to as "random access."
    *   **Memory Locality:** Storing elements contiguously often leads to better cache performance. When one element is accessed, nearby elements are often pulled into the CPU's cache, speeding up subsequent accesses to those nearby elements.

*   **Cons:**
    *   **Slow O(n) Insertion/Deletion in the Middle (Linear Time):** If you insert or delete an element anywhere but the end of the array, you have to shift all subsequent elements to make space or close the gap. This operation takes time proportional to the number of elements that need to be shifted (n), making it O(n).
        *   **Example (Insertion):** If you insert "grape" at index 1 in `["apple", "banana", "cherry"]`, "banana" and "cherry" must be shifted one position to the right to make space.
        *   **Example (Deletion):** If you delete "banana" at index 1, "cherry" must be shifted one position to the left to close the gap.
    *   **Fixed Size (in many traditional languages):** As mentioned, once created, the size is usually fixed. If you need more space, you must create a new, larger array and copy all existing elements, which is an O(n) operation. This can lead to wasted space if you allocate too much, or frequent reallocations if you allocate too little.

---

### ✅ 2. Complex Data Structures

#### Binary Trees
- [✅] **Definition:** What is a binary tree? (A tree data structure where each node has at most two children).
- [✅] **Key Terminology:** Node, Root, Parent, Child, Leaf, Subtree.
- [✅] **Traversal Techniques:**
    - [✅] **In-Order Traversal:** (Left, Root, Right). What is its primary use case? (e.g., visiting nodes in non-decreasing order in a BST).
    - [✅] **Pre-Order Traversal:** (Root, Left, Right). What is its primary use case? (e.g., creating a copy of the tree).
    - [✅] **Post-Order Traversal:** (Left, Right, Root). What is its primary use case? (e.g., deleting nodes from a tree).

> **My Explanation:**

### 1. In-Order Traversal (Left, Root, Right)

This is often the most intuitive traversal, especially for a Binary Search Tree.

*   **The Rule:** For any given node, you recursively visit its **entire left subtree**, then **process the node itself** (the "Root"), and finally recursively visit its **entire right subtree**.

*   **The "Why":** It's called "In-Order" because you process the root *in between* its left and right children.

*   **Primary Use Case:**
    To access elements in a BST in sorted order.
---

### 2. Pre-Order Traversal (Root, Left, Right)

*   **The Rule:** For any given node, you **process the node itself first**, then recursively visit its entire **left subtree**, and finally recursively visit its entire **right subtree**.

*   **The "Why":** It's called "Pre-Order" because you process the root *before* its children.

*   **Primary Use Case:**
    To create a copy of the tree. When you insert nodes into an empty tree in Pre-Order sequence, you reconstruct the *exact same tree structure*. This is useful for saving a tree's state to a file and loading it back later.

---

### 3. Post-Order Traversal (Left, Right, Root)

*   **The Rule:** For any given node, you recursively visit its entire **left subtree**, then recursively visit its entire **right subtree**, and finally, **process the node itself**.

*   **The "Why":** It's called "Post-Order" because you process the root *after* (or post) its children.

*   **Primary Use Case:**
    **To delete the nodes of a tree.** Because you process the children before the parent, you can safely delete a node without losing the pointers to its children (which would cause a memory leak). You delete the leaves first and work your way up to the root.
    - so deleting entire tree do post order, or deleting subtree first traverse to the root, then do post order deletion on that root.

---

### Summary Table

| Traversal Name | Order                | Primary Use Case                                     |
| :------------- | :------------------- | :--------------------------------------------------- |
| **In-Order**   | `Left, Root, Right`  | Getting elements from a BST in sorted order.         |
| **Pre-Order**  | `Root, Left, Right`  | Copying a tree or serializing it for reconstruction. |
| **Post-Order** | `Left, Right, Root`  | Deleting or freeing the nodes of a tree.             |

---

#### Graphs
- [✅] **Definition:** What is a graph? (A collection of nodes/vertices connected by edges).
- [✅] **Key Terminology:** Vertex, Edge, Directed vs. Undirected, Weighted vs. Unweighted, Adjacency List/Matrix.
- [✅] **Traversal Algorithms:**
    - [✅] **Breadth-First Search (BFS):** How does it work? (Explores level by level). What data structure does it use? (**Queue**).
    - [✅] **Depth-First Search (DFS):** How does it work? (Explores as far as possible down one path before backtracking). What data structure does it use? (**Stack**, can be implemented recursively or iteratively).


### Definition: What is a graph?

At its core, a graph is a data structure used to represent relationships or connections between things. It consists of two main components:

*   **Vertices (or Nodes):** These are the fundamental entities or objects within the graph.
*   **Edges:** These are the lines that connect pairs of vertices, representing a relationship between them.

Think of a social network like LinkedIn. Each person is a **vertex**, and a "connection" between two people is an **edge**. Or think of Google Maps: cities are **vertices**, and the roads between them are **edges**.

### Key Terminology

*   **Vertex (or Node):** An individual data point or object. In the map example, a vertex is a city.
*   **Edge:** The connection or relationship between two vertices. In the map example, an edge is a road connecting two cities.

*   **Directed vs. Undirected:** This describes the nature of the connection.
    *   **Undirected Graph:** Edges are two-way streets. If there's an edge between vertex A and vertex B, the relationship is mutual. Think of a Facebook friendship: if you are friends with someone, they are also friends with you. `(A) --- (B)`
    *   **Directed Graph:** Edges are one-way streets, represented with arrows. An edge from A to B doesn't imply an edge from B to A. Think of following someone on Twitter/X: you can follow them, but they don't necessarily have to follow you back. `(A) ---> (B)`

*   **Weighted vs. Unweighted:** This describes if the connections have a "cost".
    *   **Unweighted Graph:** Edges simply represent a connection. The only thing that matters is *if* a path exists. It's great for modeling "friend" networks where all friendships are equal.
    *   **Weighted Graph:** Each edge is assigned a numerical value or "weight." This weight can represent distance, time, cost, or any other metric. This is essential for applications like GPS navigation, where the goal is to find the *shortest* or *fastest* path (the path with the lowest total weight).

*   **Adjacency List vs. Adjacency Matrix:** These are the two primary ways to represent a graph in code.

    Imagine a simple graph: A is connected to B and C.

    *   **Adjacency List:** A map or dictionary where each key is a vertex, and its value is a list of the vertices it's connected to. This is very memory-efficient for graphs with few edges ("sparse" graphs).
        ```json
        // Adjacency List Representation
        {
          "A": ["B", "C"],
          "B": ["A"],
          "C": ["A"]
        }
        ```
    *   **Adjacency Matrix:** A 2D grid (an array of arrays) where `matrix[i][j] = 1` if there's an edge from vertex `i` to `j`, and `0` otherwise. This is faster for checking a specific edge's existence but uses more memory, especially for sparse graphs.
        ```
        // Adjacency Matrix Representation (A=0, B=1, C=2)
        //   A B C
        // A [0,1,1]
        // B [1,0,0]
        // C [1,0,0]
        ```

###  Traversal Algorithms

Traversal means "visiting" every vertex in a graph in a systematic way. The two most famous methods are BFS and DFS.

#### Breadth-First Search (BFS)

*   **How does it work?**
    > BFS explores the graph **level by level**. It's like ripples spreading out in a pond. Starting from a source node, it first visits all its immediate neighbors. Then, it visits all the neighbors of those neighbors, and so on. It explores "wide" before it explores "deep."

*   **What data structure does it use?** A **Queue**.
    > **Why a Queue?** A queue follows a First-In, First-Out (FIFO) principle. This is perfect for a level-by-level search.
    > 1. Add the starting vertex to the queue.
    > 2. While the queue is not empty:
    >    * Dequeue a vertex (let's call it `current`).
    >    * Visit `current`.
    >    * For each of `current`'s unvisited neighbors, add them to the *back* of the queue.
    > This process guarantees that you visit all nodes at level `k` before moving on to any nodes at level `k+1`.
    >
    > *   **Primary Use Case:** Finding the shortest path in an **unweighted** graph.

#### Depth-First Search (DFS)

*   **How does it work?**
    > DFS explores as far as possible down **one single path before backtracking**. It picks a path from the starting node and follows it to the very end (until it hits a dead end or an already visited node). Then, it backtracks to the last junction and tries the next available path. It explores "deep" before it explores "wide."

*   **What data structure does it use?** A **Stack**.
    > **Why a Stack?** A stack follows a Last-In, First-Out (LIFO) principle, which perfectly models the "go deep and backtrack" behavior.
    >
    > *   **Recursive Implementation:** The easiest way to implement DFS is with recursion. The "call stack" that programming languages use to manage function calls acts as our stack.
    >     1. Visit a vertex `current`. Mark it as visited.
    >     2. For each of `current`'s unvisited neighbors, recursively call the DFS function on that neighbor.
    >     3. When a recursive call finishes (because it hit a dead end), it "returns," effectively popping off the call stack and backtracking to the previous vertex to try another path.
    > *   **Iterative Implementation:** You can also implement DFS with an explicit `Stack` data structure, which avoids potential "stack overflow" errors on very deep graphs.
    > *   **Primary Use Cases:** Detecting cycles in a graph, topological sorting (ordering tasks with dependencies), and solving puzzles like mazes.

    ### 1. Shortest Path Algorithms

> While BFS finds the shortest path in terms of the number of edges, these algorithms find the shortest path in **weighted** graphs, where "shortest" means "lowest total weight."

---

### Dijkstra's Algorithm

#### The High-Level Goal & Analogy

**Goal:** To find the shortest path from a single starting vertex to every other vertex in a weighted graph.

**Key Constraint:** It only works correctly when all edge weights are **non-negative**. You can't have a road that takes "-5 minutes" to travel.

### How It's Implemented: 

To make this work in code, we need three key data structures.

#### Data Structures

1.  **Distances Map/Array:** This stores the shortest distance we have found *so far* from the start vertex to every other vertex.
    *   We initialize the start vertex's distance to `0`.
    *   We initialize every other vertex's distance to `Infinity`, because we haven't found a path to them yet.
    *   `distances = { A: 0, B: Infinity, C: Infinity, D: Infinity }`

2.  **Priority Queue:** This is the secret sauce. A priority queue stores vertices and lets us efficiently ask one question: **"Of all the vertices I can currently reach but haven't finalized, which one is closest to the start?"** Dijkstra's is a greedy algorithm. This means that at every single step, it makes the choice that looks best at that moment.  by always processing the node with the lowest total cost first (thanks to the priority queue), you guarantee that you find and finalize the shortest path to that specific node. The priority queue enforces the greedy choice when you want to visit a new node.

3.  **Visited Set:** A set that keeps track of vertices for which we have already found the *final, guaranteed* shortest path. Once a vertex is in this set, we will never need to look at it again.

#### The Recipe (The Algorithm Steps)

Let's use a simple example graph. **Start = A**.

*   `A -> B (weight 1)`
*   `A -> D (weight 4)`
*   `B -> C (weight 2)`
*   `B -> D (weight 6)`
*   `D -> C (weight 3)`

**Step 0: Initialization**
*   `distances = { A: 0, B: Infinity, C: Infinity, D: Infinity }`
*   `priority_queue` contains `{ A with priority 0 }`
*   `visited = {}` (Empty)

**Step 1: First Iteration**
*   The loop begins. **Extract the vertex with the lowest priority** from the `priority_queue`.
    *   `current_vertex` = **A** (priority 0).
*   Add **A** to the `visited` set. We have now finalized the shortest path to A (it's 0).
*   **Check A's unvisited neighbors:** B and D.
    *   **For B:** The distance to B *through A* is `distances[A] + weight(A->B)` => `0 + 1 = 1`.
        *   Is `1` less than the current `distances[B]` (which is `Infinity`)? Yes.
        *   **Update:** `distances[B] = 1`. Add `{B with priority 1}` to the `priority_queue`.
    *   **For D:** The distance to D *through A* is `distances[A] + weight(A->D)` => `0 + 4 = 4`.
        *   Is `4` less than `distances[D]` (`Infinity`)? Yes.
        *   **Update:** `distances[D] = 4`. Add `{D with priority 4}` to the `priority_queue`.
*   _End of Iteration 1 State:_
    *   `distances = { A: 0, B: 1, C: Infinity, D: 4 }`
    *   `priority_queue` contains `{ B: 1, D: 4 }`

**Step 2: Second Iteration**
*   **Extract the vertex with the lowest priority**:
    *   `current_vertex` = **B** (priority 1).
*   Add **B** to the `visited` set.
*   **Check B's unvisited neighbors:** C and D.
    *   **For C:** The distance to C *through B* is `distances[B] + weight(B->C)` => `1 + 2 = 3`.
        *   Is `3` less than `distances[C]` (`Infinity`)? Yes.
        *   **Update:** `distances[C] = 3`. Add `{C with priority 3}` to the `priority_queue`.
    *   **For D:** The distance to D *through B* is `distances[B] + weight(B->D)` => `1 + 6 = 7`.
        *   Is `7` less than `distances[D]` (`4`)? No. The path we already found (`A->D`) is better. **Do nothing.**
*   _End of Iteration 2 State:_
    *   `distances = { A: 0, B: 1, C: 3, D: 4 }`
    *   `priority_queue` contains `{ C: 3, D: 4 }`

**Step 3: Third Iteration**
*   **Extract the vertex with the lowest priority**:
    *   `current_vertex` = **C** (priority 3).
*   Add **C** to the `visited` set.
*   **Check C's unvisited neighbors:** None. (Or if it had neighbors, we'd check them).
*   _End of Iteration 3 State:_
    *   `distances = { A: 0, B: 1, C: 3, D: 4 }`
    *   `priority_queue` contains `{ D: 4 }`

**Step 4: Fourth Iteration**
*   **Extract the vertex with the lowest priority**:
    *   `current_vertex` = **D** (priority 4).
*   Add **D** to `visited`.
*   **Check D's unvisited neighbors:** C. But C is already in `visited`, so we ignore it.

**Step 5: Finish**
*   The `priority_queue` is now empty. The algorithm terminates.
*   The final `distances` map `{ A: 0, B: 1, C: 3, D: 4 }` contains the shortest path from A to every other vertex.

#### A\* (A-Star) Search Algorithm

*   **What it is:** A "smarter" version of Dijkstra's. It adds a **heuristic**—an educated guess—to prioritize paths that are heading in the right direction.
*   **How it works:** In addition to the actual cost from the start (like Dijkstra), it also estimates the cost to get from the current vertex *to the destination*. It prioritizes vertices with the lowest `(cost from start) + (estimated cost to end)`.
*   **Use Case:** Video game pathfinding for characters. Why explore a path going away from the target when you can make an educated guess about the right direction?
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