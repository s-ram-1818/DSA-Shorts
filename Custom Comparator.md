
# C++ Comparators and Priority Queue

This document covers different ways to implement **custom comparators** in C++ and how to use them with `std::sort` and `std::priority_queue`.

---

## **1. Comparator Basics**
Comparators are used to define custom sorting rules in C++ containers like `std::sort` and `std::priority_queue`.

- Default sorting in C++ is **ascending order** using `<` operator.
- Comparators return:
  - `true` → if first element should come **before** the second.
  - `false` → otherwise.

**Syntax:**
```cpp
bool comparator(const Type &a, const Type &b) {
    return a < b; // ascending order
}
```

---

## **2. Different Types of Comparators**

### **A. Lambda Comparator**
#### 1️⃣ Pass by Value
```cpp
vector<pair<char,int>> v = {{'a',2},{'b',5},{'c',3}};
sort(v.begin(), v.end(), [](pair<char,int> a, pair<char,int> b) {
    return a.second > b.second; // descending by second
});
```

#### 2️⃣ Pass by Const Reference (Best for performance)
```cpp
sort(v.begin(), v.end(), [](const pair<char,int> &a, const pair<char,int> &b) {
    return a.second > b.second;
});
```

---

### **B. Free Function Comparator**
```cpp
bool cmpFunction(pair<char,int> a, pair<char,int> b) {
    return a.second > b.second;
}

sort(v.begin(), v.end(), cmpFunction);
```

---

### **C. Functor (Struct with `operator()`)**
Acts like a function object.
```cpp
struct CmpFunctor {
    bool operator()(const pair<char,int> &a, const pair<char,int> &b) const {
        return a.second > b.second;
    }
};

sort(v.begin(), v.end(), CmpFunctor());
```

---

### **D. Static Comparator Inside a Class**
Static functions don't have a hidden `this` pointer, so they can be passed directly to `std::sort`.

```cpp
struct Student {
    string name;
    int marks;

    static bool cmpByMarks(const Student &a, const Student &b) {
        if (a.marks == b.marks) return a.name < b.name; // Secondary sort by name
        return a.marks > b.marks;
    }
};

vector<Student> students = {
    {"Ram", 85},
    {"Sita", 92},
    {"Hari", 85}
};

sort(students.begin(), students.end(), Student::cmpByMarks);
```

---

## **3. Priority Queue with Custom Comparator**

### **Default Priority Queue Behavior**
- By default, `std::priority_queue` is a **Max Heap**.

**Syntax:**
```cpp
priority_queue<int> maxHeap; // largest element at top
priority_queue<int, vector<int>, greater<int>> minHeap; // smallest element at top
```

---

### **Custom Comparator for Min Heap of Pairs**
```cpp
class ComparePairs {
public:
    bool operator()(const pair<char, int> &a, const pair<char, int> &b) {
        return a.second > b.second; 
        // Min-heap: smaller 'second' value has higher priority
    }
};

priority_queue<pair<char, int>, vector<pair<char, int>>, ComparePairs> pq;

pq.push({'a', 2});
pq.push({'b', 5});
pq.push({'c', 3});

while (!pq.empty()) {
    cout << pq.top().first << " " << pq.top().second << "\n";
    pq.pop();
}
```
**Output:**
```
a 2
c 3
b 5
```

---

## **4. Summary Table**

| Comparator Type      | Usage | Notes |
|----------------------|-------|-------|
| **Lambda**           | `sort(v.begin(), v.end(), [](const auto &a, const auto &b){ return a.second > b.second; });` | Best for inline simple logic |
| **Free Function**    | `sort(v.begin(), v.end(), cmpFunction);` | Easy to reuse |
| **Functor (Struct)** | `sort(v.begin(), v.end(), CmpFunctor());` | Good for reusable, complex logic |
| **Static Member**    | `sort(v.begin(), v.end(), ClassName::cmpFunction);` | Clean when related to a specific class |
| **Priority Queue**   | `priority_queue<Type, vector<Type>, Comparator>` | Min/Max Heap customization |

---

## **Key Points**
- Use **const references** in comparator parameters to avoid unnecessary copying.
- For `priority_queue`, remember **default is Max Heap**, so invert comparator for Min Heap.
- For **tie-breaking** logic, compare secondary fields inside comparator.
- Prefer **lambdas** for short, simple comparators.

---

## **Example: Sorting Students**
```cpp
for (auto &st : students) {
    cout << st.name << " " << st.marks << "\n";
}
```

---

This concludes the notes on **comparators** and **priority queues** in C++.
