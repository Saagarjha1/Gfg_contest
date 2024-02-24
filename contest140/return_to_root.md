# Return to root Problem

This problem is about traversing directories based on given commands and determining the depth of the current directory.

## C++ Solution

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    int ReturnToRoot(int N, vector<string> &M) {
        stack<string> s; // Stack to keep track of directories
        for(int i = 0; i < M.size(); i++) {
            if(M[i] == "../") {
                if(!s.empty()) {
                    s.pop(); // Move one directory up
                }
            }
            else if(M[i] == "./") {
                continue; // Current directory, nothing to do
            }
            else {
                s.push(M[i]); // Push the directory onto the stack
            }
        }
        return s.size(); // Size of stack represents the depth of current directory
    }
};

