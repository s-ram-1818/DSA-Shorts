
string s;                      // Empty string
string s("hello");             // From C-string literal
string s(5, 'x');              // "xxxxx"
string s2(s);                  // Copy constructor
string s3 = s.substr(1, 3);    // "ell"


s.size();        // Number of characters
s.length();      // Same as size()
s.empty();       // true if empty
s.capacity();    // Current allocated storage
s.reserve(50);   // Reserve at least 50 chars
s.clear();       // Remove all chars


s[i];            // Access (no bounds check)
s.at(i);         // Access (with bounds check)
s.front();       // First char
s.back();        // Last char

s.append("abc");             // Append string
s.append("abc", 2);          // Append first 2 chars
s += "xyz";                  // Append operator
s.push_back('z');            // Append single char
s.pop_back();                // Remove last char

s.replace(pos, len, "abc");  // Replace substring
s.replace(itr1, itr2, "abc");// Replace range

s.insert(pos, "abc");        // Insert at position
s.insert(pos, 3, 'x');       // Insert n copies
s.insert(itr, 'x');          // Insert at iterator
s.insert(itr, 3, 'x');       // Insert multiple

s.erase();                   // Erase all
s.erase(idx);                // From idx to end
s.erase(idx, k);             // k chars from idx
s.erase(itr);                // At iterator
s.erase(first, last);        // Range erase

s.find("abc");               // First occurrence
s.find("abc", start);        // Start from index
s.rfind("abc");              // Last occurrence
s.find_first_of("abc");      // First match of any char
s.find_last_of("abc");       // Last match of any char
s.find_first_not_of("abc");  // First NOT in set
s.find_last_not_of("abc");   // Last NOT in set

s.substr(pos);               // From pos to end
s.substr(pos, len);          // len chars from pos

s == "abc";                  // Equality
s.compare("abc");            // 0 = equal, <0 smaller, >0 greater
s.compare(pos, len, "abc");  // Compare substring

stoi(s);     // String → int
stol(s);     // String → long
stoll(s);    // String → long long
stof(s);     // String → float
stod(s);     // String → double
stold(s);    // String → long double

to_string(123);    // int → string
to_string(3.14);   // double → string

s.begin();     // Iterator to first char
s.end();       // Iterator to one past last char
s.rbegin();    // Reverse iterator to last char
s.rend();      // Reverse iterator before first char

getline(cin, s);    // Read line
swap(s1, s2);       // Swap strings
