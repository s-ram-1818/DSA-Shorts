# 📌 C++ `std::string` STL – Complete Cheat Sheet (Mobile-Friendly)

---

<details>
<summary>1️⃣ Initialization</summary>

| Function / Syntax                 | Description                              | Example                                   | Time Complexity |
|------------------------------------|------------------------------------------|-------------------------------------------|-----------------|
| `string s;`                        | Empty string                             | `string s;`                               | O(1)            |
| `string s("hello");`               | From C-string literal                    | `string s("hi");`                         | O(n)            |
| `string s(5, 'x');`                 | Fill with n copies of char               | `string s(5, 'a'); // "aaaaa"`            | O(n)            |
| `string s2(s);`                     | Copy constructor                         | `string s2(s1);`                          | O(n)            |
| `string s3 = s.substr(1, 3);`       | Substring constructor                    | `"hello".substr(1,3) // "ell"`            | O(k)            |

</details>

---

<details>
<summary>2️⃣ Size & Capacity</summary>

| Function         | Description                      | Example           | Time Complexity |
|------------------|----------------------------------|-------------------|-----------------|
| `size()`         | Number of characters             | `s.size()`        | O(1)            |
| `length()`       | Same as size()                   | `s.length()`      | O(1)            |
| `empty()`        | Check if empty                   | `s.empty()`       | O(1)            |
| `capacity()`     | Allocated storage size           | `s.capacity()`    | O(1)            |
| `reserve(n)`     | Reserve at least n capacity      | `s.reserve(50)`   | O(1) amortized  |
| `clear()`        | Remove all chars                 | `s.clear()`       | O(n)            |

</details>

---

<details>
<summary>3️⃣ Element Access</summary>

| Function       | Description                  | Example        | Time Complexity |
|----------------|------------------------------|----------------|-----------------|
| `s[i]`         | Access (no bounds check)     | `s[2]`         | O(1)            |
| `at(i)`        | Access (with bounds check)   | `s.at(2)`      | O(1)            |
| `front()`      | First char                   | `s.front()`    | O(1)            |
| `back()`       | Last char                    | `s.back()`     | O(1)            |

</details>

---

<details>
<summary>4️⃣ Modifiers</summary>

**Appending**
| Function                | Description              | Example                | TC        |
|-------------------------|--------------------------|------------------------|-----------|
| `append("abc")`         | Append string            | `s.append("abc")`      | O(k)      |
| `append("abc", 2)`      | Append first 2 chars     | `s.append("abc", 2)`   | O(k)      |
| `+= "xyz"`              | Append via operator      | `s += "xyz"`           | O(k)      |
| `push_back('z')`        | Append one char          | `s.push_back('z')`     | O(1)      |
| `pop_back()`            | Remove last char         | `s.pop_back()`         | O(1)      |

**Inserting**
| Function                       | Description           | Example                       | TC        |
|--------------------------------|-----------------------|--------------------------------|-----------|
| `insert(pos, "abc")`           | Insert at index       | `s.insert(2,"hi")`             | O(n)      |
| `insert(pos, 3, 'x')`          | Insert multiple chars | `s.insert(1,3,'a')`            | O(n)      |
| `insert(itr, 'x')`             | Insert at iterator    | `s.insert(s.begin(),'a')`      | O(n)      |

**Replacing**
| Function                       | Description           | Example                       | TC        |
|--------------------------------|-----------------------|--------------------------------|-----------|
| `replace(pos, len, "abc")`     | Replace substring     | `s.replace(1,3,"xy")`          | O(n)      |
| `replace(itr1, itr2, "abc")`   | Replace range         | `s.replace(s.begin(), s.begin()+2, "hi")` | O(n) |

**Erasing**
| Function                 | Description              | Example                  | TC    |
|--------------------------|--------------------------|--------------------------|-------|
| `erase()`                | Erase all                | `s.erase()`              | O(n)  |
| `erase(idx)`             | From idx to end          | `s.erase(3)`             | O(n)  |
| `erase(idx, k)`          | Erase k chars from idx   | `s.erase(2,4)`           | O(n)  |
| `erase(itr)`             | Erase at iterator        | `s.erase(s.begin())`     | O(n)  |
| `erase(first,last)`      | Erase range              | `s.erase(s.begin(), s.begin()+3)` | O(n) |

</details>

---

<details>
<summary>5️⃣ Searching</summary>

| Function                 | Description                     | Example                     | TC        |
|--------------------------|---------------------------------|-----------------------------|-----------|
| `find("abc")`            | First occurrence                | `s.find("hi")`               | O(n*k)    |
| `find("abc", start)`     | Start from index                 | `s.find("hi", 3)`             | O(n)      |
| `rfind("abc")`           | Last occurrence                  | `s.rfind("hi")`               | O(n*k)    |
| `find_first_of("abc")`   | First match of any char           | `s.find_first_of("xyz")`      | O(n*k)    |
| `find_last_of("abc")`    | Last match of any char            | `s.find_last_of("xyz")`       | O(n*k)    |
| `find_first_not_of("abc")`| First NOT in set                 | `s.find_first_not_of("aeiou")`| O(n*k)    |
| `find_last_not_of("abc")` | Last NOT in set                  | `s.find_last_not_of("aeiou")` | O(n*k)    |

</details>

---

<details>
<summary>6️⃣ Substrings</summary>

| Function         | Description                | Example                      | TC    |
|------------------|----------------------------|------------------------------|-------|
| `substr(pos)`    | From pos to end            | `"hello".substr(2)` // "llo" | O(k)  |
| `substr(pos, len)`| len chars from pos        | `"hello".substr(1,3)` // "ell"| O(k)  |

</details>

---

<details>
<summary>7️⃣ Comparison</summary>

| Function                     | Description                  | Example                          | TC    |
|------------------------------|------------------------------|-----------------------------------|-------|
| `==`                         | Equality                     | `s == "abc"`                      | O(n)  |
| `compare("abc")`             | Lexicographic compare         | `s.compare("abc")`                | O(n)  |
| `compare(pos, len, "abc")`   | Compare substring             | `s.compare(0,2,"ab")`              | O(k)  |

</details>

---

<details>
<summary>8️⃣ Conversions</summary>

| Function        | Description        | Example                  | TC  |
|-----------------|--------------------|--------------------------|-----|
| `stoi(s)`       | String → int       | `stoi("123")`            | O(n)|
| `stol(s)`       | String → long      | `stol("12345")`          | O(n)|
| `stoll(s)`      | String → long long | `stoll("123456789")`     | O(n)|
| `stof(s)`       | String → float     | `stof("3.14")`           | O(n)|
| `stod(s)`       | String → double    | `stod("3.14159")`        | O(n)|
| `to_string(x)`  | Number → string    | `to_string(42)`          | O(n)|

</details>

---

<details>
<summary>9️⃣ Iterators</summary>

| Function      | Description                         | Example                  | TC |
|---------------|-------------------------------------|--------------------------|----|
| `begin()`     | Iterator to first char              | `auto it = s.begin();`   | O(1)|
| `end()`       | Iterator to one past last char      | `auto it = s.end();`     | O(1)|
| `rbegin()`    | Reverse iterator to last char       | `auto it = s.rbegin();`  | O(1)|
| `rend()`      | Reverse iterator before first char  | `auto it = s.rend();`    | O(1)|

</details>

---

<details>
<summary>🔟 Non-member Functions</summary>

| Function        | Description                 | Example              | TC   |
|-----------------|-----------------------------|----------------------|------|
| `getline(cin,s)`| Read line from input stream  | `getline(cin, s);`   | O(n) |
| `swap(s1,s2)`   | Swap two strings             | `swap(a,b);`         | O(1) |

</details>

---

## 📝 Notes
- **`npos`** = `string::npos` means “not found” (max `size_t` value).
- **Dynamic growth** — string resizes automatically.
- **0-based indexing**.
- **Iterator invalidation** — insert/erase can make iterators invalid.

