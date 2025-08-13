# 📌 C++ String STL – Easy Reference

---

<details>
<summary>1️⃣ Initialization</summary>

| Syntax / Function            | Meaning                              | Example                                   | Output     | TC   |
|------------------------------|---------------------------------------|-------------------------------------------|------------|------|
| `string s;`                  | Create an empty string               | `string s;`                               | `""`       | O(1) |
| `string s("hello");`         | Create from a C-style string         | `string s("hi");`                         | `"hi"`     | O(n) |
| `string s(5, 'x');`          | Fill with n copies of a char         | `string s(5, 'a');`                       | `"aaaaa"`  | O(n) |
| `string s2(s);`              | Copy constructor (duplicate string)  | `string s2("abc");`                       | `"abc"`    | O(n) |
| `string s3 = s.substr(1, 3);`| Create from a substring               | `"hello".substr(1,3)`                     | `"ell"`    | O(k) |

</details>

---

<details>
<summary>2️⃣ Size & Capacity</summary>

| Syntax / Function    | Meaning                                    | Example               | Output        | TC   |
|---------------------|--------------------------------------------|----------------------|---------------|------|
| `size()`             | Number of characters                       | `string("abc").size()` | `3`          | O(1) |
| `length()`           | Same as size()                              | `string("abc").length()` | `3`       | O(1) |
| `empty()`            | Check if string is empty                    | `string("").empty()`  | `true`       | O(1) |
| `capacity()`         | Allocated memory (may be more than size)   | `s.capacity()`        | *(varies)*   | O(1) |
| `reserve(n)`         | Reserve memory at least n                  | `s.reserve(50)`       | *(no output)*| O(1) amortized |
| `clear()`            | Remove all characters                       | `string("abc").clear()` | `""`       | O(n) |

</details>

---

<details>
<summary>3️⃣ Element Access</summary>

| Syntax / Function    | Meaning                                    | Example               | Output  | TC   |
|---------------------|--------------------------------------------|----------------------|---------|------|
| `s[i]`               | Access character at index (no bounds check)| `string("abc")[1]`   | `'b'`   | O(1) |
| `at(i)`              | Access character with bounds check         | `string("abc").at(1)`| `'b'`   | O(1) |
| `front()`            | First character                             | `string("abc").front()` | `'a'` | O(1) |
| `back()`             | Last character                              | `string("abc").back()`  | `'c'` | O(1) |

</details>

---

<details>
<summary>4️⃣ Modifiers</summary>

**Appending Strings/Chars**  

| Syntax / Function | Meaning                       | Example                        | Output       | TC   |
|-----------------|--------------------------------|--------------------------------|-------------|------|
| `append("abc")`  | Append string                  | `string("hi").append("abc")`   | `"hiabc"`   | O(k) |
| `append("abc",2)`| Append first 2 chars           | `string("hi").append("abc",2)` | `"hiab"`    | O(k) |
| `+= "xyz"`       | Append using operator          | `string("hi") += "xyz"`        | `"hixyz"`   | O(k) |
| `push_back('z')` | Append single character        | `string("hi").push_back('z')`  | `"hiz"`     | O(1) |
| `pop_back()`     | Remove last character          | `string("hiz").pop_back()`     | `"hi"`      | O(1) |

**Inserting**  

| Syntax / Function | Meaning                       | Example                        | Output       | TC   |
|-----------------|--------------------------------|--------------------------------|-------------|------|
| `insert(pos,"abc")`| Insert string at index        | `string("hi").insert(1,"abc")` | `"habci"`  | O(n) |
| `insert(pos,3,'x')`| Insert multiple chars         | `string("hi").insert(1,3,'a')` | `"haaai"` | O(n) |
| `insert(itr,'x')`  | Insert at iterator            | `string("hi").insert(s.begin(),'a')` | `"ahi"` | O(n) |

**Replacing**  

| Syntax / Function | Meaning                       | Example                        | Output       | TC   |
|-----------------|--------------------------------|--------------------------------|-------------|------|
| `replace(pos,len,"abc")` | Replace substring        | `string("hello").replace(1,3,"xy")` | `"hxyo"` | O(n) |
| `replace(itr1,itr2,"abc")` | Replace range           | `string("hello").replace(s.begin(), s.begin()+2, "hi")` | `"hillo"` | O(n) |

**Erasing**  

| Syntax / Function | Meaning                       | Example                        | Output       | TC   |
|-----------------|--------------------------------|--------------------------------|-------------|------|
| `erase()`        | Remove all characters           | `string("abc").erase()`        | `""`        | O(n) |
| `erase(idx)`     | Remove from index to end        | `string("abcdef").erase(3)`    | `"abc"`     | O(n) |
| `erase(idx,k)`   | Remove k characters from idx    | `string("abcdef").erase(2,4)`  | `"ab"`      | O(n) |
| `erase(itr)`     | Remove at iterator              | `string("abc").erase(s.begin())` | `"bc"`   | O(n) |
| `erase(first,last)` | Remove range                | `string("abcdef").erase(s.begin(), s.begin()+3)` | `"def"` | O(n) |

</details>

---

<details>
<summary>5️⃣ Searching</summary>

| Syntax / Function           | Meaning                                         | Example                                      | Output | TC    |
|-----------------------------|-------------------------------------------------|---------------------------------------------|--------|-------|
| `find("abc")`               | Find first occurrence of substring             | `string("hiabcabc").find("abc")`           | `2`    | O(n*k)|
| `find("abc", start)`        | Find first occurrence starting at index `start`| `string("hiabcabc").find("abc",3)`         | `5`    | O(n)  |
| `rfind("abc")`              | Find last occurrence of substring              | `string("abcabc").rfind("abc")`            | `3`    | O(n*k)|
| `find_first_of("abc")`      | First matching any character in set            | `string("xyzay").find_first_of("abc")`     | `3`    | O(n*k)|
| `find_last_of("abc")`       | Last matching any character in set             | `string("xyzayc").find_last_of("abc")`     | `5`    | O(n*k)|
| `find_first_not_of("abc")`  | First character NOT in set                      | `string("aaabz").find_first_not_of("abc")` | `4`    | O(n*k)|
| `find_last_not_of("abc")`   | Last character NOT in set                       | `string("zaaa").find_last_not_of("abc")`   | `0`    | O(n*k)|

</details>

---

<details>
<summary>6️⃣ Substrings</summary>

| Syntax / Function      | Meaning                              | Example                        | Output  | TC   |
|------------------------|--------------------------------------|--------------------------------|---------|------|
| `substr(pos)`          | Take substring from `pos` to end     | `string("hello").substr(2)`    | `"llo"` | O(k) |
| `substr(pos,len)`      | Take `len` characters from `pos`     | `string("hello").substr(1,3)`  | `"ell"` | O(k) |

</details>

---

<details>
<summary>7️⃣ Comparison</summary>

| Syntax / Function            | Meaning                               | Example                               | Output | TC   |
|-------------------------------|---------------------------------------|---------------------------------------|--------|------|
| `==`                          | Check if strings are equal            | `string("abc") == "abc"`             | `true` | O(n) |
| `compare("abc")`              | Lexicographic comparison              | `string("abc").compare("abc")`       | `0`    | O(n) |
| `compare(pos,len,"abc")`      | Compare substring with another string | `string("abcd").compare(0,2,"ab")`  | `0`    | O(k) |

</details>

---

<details>
<summary>8️⃣ Conversions</summary>

| Syntax / Function        | Meaning                       | Example                  | Output      | TC   |
|--------------------------|--------------------------------|--------------------------|-------------|------|
| `stoi(s)`                | Convert string → int           | `stoi("123")`            | `123`       | O(n) |
| `stol(s)`                | Convert string → long          | `stol("12345")`          | `12345`     | O(n) |
| `stoll(s)`               | Convert string → long long     | `stoll("123456789")`     | `123456789` | O(n) |
| `stof(s)`                | Convert string → float         | `stof("3.14")`           | `3.14`      | O(n) |
| `stod(s)`                | Convert string → double        | `stod("3.14159")`        | `3.14159`   | O(n) |
| `to_string(x)`           | Convert number → string        | `to_string(42)`          | `"42"`      | O(n) |

</details>

---

<details>
<summary>9️⃣ Iterators</summary>

| Syntax / Function | Meaning                                  | Example                          | Output (first element) | TC   |
|------------------|-----------------------------------------|---------------------------------|-----------------------|------|
| `begin()`         | Iterator to first character             | `*string("abc").begin()`        | `'a'`                 | O(1) |
| `end()`           | Iterator one past last character        | `*(--string("abc").end())`     | `'c'`                 | O(1) |
| `rbegin()`        | Reverse iterator to last character      | `*string("abc").rbegin()`      | `'c'`                 | O(1) |
| `rend()`          | Reverse iterator before first character | `*(--string("abc").rend())`    | `'a'`                 | O(1) |

</details>

---

<details>
<summary>🔟 Non-member Functions</summary>

| Syntax / Function       | Meaning                       | Example                                      | Output              | TC   |
|-------------------------|-------------------------------|---------------------------------------------|-------------------|------|
| `getline(cin,s)`        | Read entire line from input    | *(input: Hello World)* `getline(cin,s);`    | `"Hello World"`    | O(n) |
| `swap(s1,s2)`           | Swap two strings               | `swap(a,b)` where a=`"hi"`, b=`"bye"`      | a=`"bye"`, b=`"hi"`| O(1) |

</details>
