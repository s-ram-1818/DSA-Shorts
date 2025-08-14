| Category                | Syntax / Function             | Meaning / Use                                  | Example                                       | Output              | TC      |
| ----------------------- | ----------------------------- | ---------------------------------------------- | --------------------------------------------- | ------------------- | ------- |
| **Initialization**      | `string s;`                   | Empty string                                   | `string s;`                                   | `""`                | O(1)    |
|                         | `string s("hi");`             | From C-style string                            | `string s("hi");`                             | `"hi"`              | O(n)    |
|                         | `string s(5, 'a');`           | Fill with n copies of char                     | `string s(5, 'a');`                           | `"aaaaa"`           | O(n)    |
|                         | `string s2(s);`               | Copy constructor                               | `string s2("abc");`                           | `"abc"`             | O(n)    |
|                         | `string s3 = s.substr(1, 3);` | From substring                                 | `"hello".substr(1,3)`                         | `"ell"`             | O(k)    |
| **Size & Capacity**     | `s.size()` / `s.length()`     | Length                                         | `string("abc").size()`                        | `3`                 | O(1)    |
|                         | `s.empty()`                   | Check if empty                                 | `string("").empty()`                          | `true`              | O(1)    |
|                         | `s.capacity()`                | Allocated storage                              | —                                             | varies              | O(1)    |
|                         | `s.reserve(n)`                | Reserve memory                                 | `s.reserve(50)`                               | —                   | O(1)\*  |
|                         | `s.clear()`                   | Remove all chars                               | `string("abc").clear()`                       | `""`                | O(n)    |
| **Element Access**      | `s[i]`                        | Access char (no bounds check)                  | `string("abc")[1]`                            | `'b'`               | O(1)    |
|                         | `s.at(i)`                     | Access with bounds check                       | `string("abc").at(1)`                         | `'b'`               | O(1)    |
|                         | `s.front()`                   | First char                                     | `string("abc").front()`                       | `'a'`               | O(1)    |
|                         | `s.back()`                    | Last char                                      | `string("abc").back()`                        | `'c'`               | O(1)    |
| **Modifiers – Append**  | `s.append("abc")`             | Append string                                  | `string("hi").append("abc")`                  | `"hiabc"`           | O(k)    |
|                         | `s.append("abc", 2)`          | Append first 2 chars                           | `"hi".append("abc", 2)`                       | `"hiab"`            | O(k)    |
|                         | `s += "xyz"`                  | Append using operator                          | `string("hi") += "xyz"`                       | `"hixyz"`           | O(k)    |
|                         | `s.push_back('z')`            | Append single char                             | `"hi".push_back('z')`                         | `"hiz"`             | O(1)    |
|                         | `s.pop_back()`                | Remove last char                               | `"hiz".pop_back()`                            | `"hi"`              | O(1)    |
| **Modifiers – Insert**  | `s.insert(pos,"abc")`         | Insert string at index                         | `"hi".insert(1,"abc")`                        | `"habci"`           | O(n)    |
|                         | `s.insert(pos,3,'a')`         | Insert multiple chars                          | `"hi".insert(1,3,'a')`                        | `"haaai"`           | O(n)    |
|                         | `s.insert(it,'a')`            | Insert at iterator                             | `"hi".insert(s.begin(),'a')`                  | `"ahi"`             | O(n)    |
| **Modifiers – Replace** | `s.replace(pos,len,"abc")`    | Replace substring                              | `"hello".replace(1,3,"xy")`                   | `"hxyo"`            | O(n)    |
|                         | `s.replace(it1,it2,"abc")`    | Replace range                                  | `"hello".replace(s.begin(),s.begin()+2,"hi")` | `"hillo"`           | O(n)    |
| **Modifiers – Erase**   | `s.erase()`                   | Remove all chars                               | `"abc".erase()`                               | `""`                | O(n)    |
|                         | `s.erase(idx)`                | Remove from idx to end                         | `"abcdef".erase(3)`                           | `"abc"`             | O(n)    |
|                         | `s.erase(idx,k)`              | Remove k chars from idx                        | `"abcdef".erase(2,4)`                         | `"ab"`              | O(n)    |
|                         | `s.erase(it)`                 | Remove at iterator                             | `"abc".erase(s.begin())`                      | `"bc"`              | O(n)    |
|                         | `s.erase(it1,it2)`            | Remove range                                   | `"abcdef".erase(s.begin(),s.begin()+3)`       | `"def"`             | O(n)    |
| **Searching**           | `s.find("abc")`               | First occurrence                               | `"hiabcabc".find("abc")`                      | `2`                 | O(n\*k) |
|                         | `s.find("abc", start)`        | First occurrence from `start`                  | `"hiabcabc".find("abc",3)`                    | `5`                 | O(n)    |
|                         | `s.rfind("abc")`              | Last occurrence                                | `"abcabc".rfind("abc")`                       | `3`                 | O(n\*k) |
|                         | `s.find_first_of("abc")`      | First match of any char in set                 | `"xyzay".find_first_of("abc")`                | `3`                 | O(n\*k) |
|                         | `s.find_last_of("abc")`       | Last match of any char in set                  | `"xyzayc".find_last_of("abc")`                | `5`                 | O(n\*k) |
|                         | `s.find_first_not_of("abc")`  | First char NOT in set                          | `"aaabz".find_first_not_of("abc")`            | `4`                 | O(n\*k) |
|                         | `s.find_last_not_of("abc")`   | Last char NOT in set                           | `"zaaa".find_last_not_of("abc")`              | `0`                 | O(n\*k) |
| **Substrings**          | `s.substr(pos)`               | From pos to end                                | `"hello".substr(2)`                           | `"llo"`             | O(k)    |
|                         | `s.substr(pos,len)`           | `len` chars from pos                           | `"hello".substr(1,3)`                         | `"ell"`             | O(k)    |
| **Comparison**          | `s1 == s2`                    | Equality                                       | `"abc" == "abc"`                              | `true`              | O(n)    |
|                         | `s.compare("abc")`            | Lexicographic                                  | `"abc".compare("abc")`                        | `0`                 | O(n)    |
|                         | `s.compare(pos,len,"abc")`    | Compare substring                              | `"abcd".compare(0,2,"ab")`                    | `0`                 | O(k)    |
| **Conversions**         | `stoi(s)`                     | String → int                                   | `stoi("123")`                                 | `123`               | O(n)    |
|                         | `stol(s)`                     | String → long                                  | `stol("12345")`                               | `12345`             | O(n)    |
|                         | `stoll(s)`                    | String → long long                             | `stoll("123456789")`                          | `123456789`         | O(n)    |
|                         | `stof(s)`                     | String → float                                 | `stof("3.14")`                                | `3.14`              | O(n)    |
|                         | `stod(s)`                     | String → double                                | `stod("3.14159")`                             | `3.14159`           | O(n)    |
|                         | `to_string(x)`                | Number → string                                | `to_string(42)`                               | `"42"`              | O(n)    |
| **Iterators**           | `s.begin()`                   | Iterator to first char                         | `*string("abc").begin()`                      | `'a'`               | O(1)    |
|                         | `s.end()`                     | Iterator after last char                       | `*(--string("abc").end())`                    | `'c'`               | O(1)    |
|                         | `s.rbegin()`                  | Reverse iterator to last char                  | `*string("abc").rbegin()`                     | `'c'`               | O(1)    |
|                         | `s.rend()`                    | Reverse iterator before first char             | —                                             | —                   | O(1)    |
| **Non-member**          | `getline(cin,s)`              | Read whole line                                | *(input: Hello World)* → `"Hello World"`      | —                   | O(n)    |
|                         | `swap(s1,s2)`                 | Swap two strings                               | `swap(a,b)` where a=`"hi"`, b=`"bye"`         | a=`"bye"`, b=`"hi"` | O(1)    |
| **Other Useful**        | `s.resize(n)`                 | Resize string (trunc/pad with `'\0'`)          | `"abc".resize(5)`                             | `"abc\0\0"`         | O(n)    |
|                         | `s.shrink_to_fit()`           | Reduce capacity to size                        | —                                             | —                   | O(n)    |
|                         | `s.c_str()`                   | Get const char\* (null-terminated)             | —                                             | —                   | O(1)    |
|                         | `s.data()`                    | Pointer to char array (C++17: includes `'\0'`) | —                                             | —                   | O(1)    |
|                         | `s.copy(buf,len,pos)`         | Copy substring into buffer                     | —                                             | —                   | O(k)    |
