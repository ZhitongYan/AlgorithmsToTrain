## Welcome to GitHub Pages

Hi friend! Welcome to my algorithms blog! (It doesn't seem to be a "real" blog though. XD)

I'm Zhitong, an idealist, a dreamer, and a programmer. The reason why I finally open this little blog is that DP problems has always been the headache. Another reason is that I want to do something good to both me myself and others like me.

Talk is cheap, just begin the travel of algorithms :)

### Longest Palindromic Substring

This is a classic problem.

Version-1 "Brute Force"
  First, find out all possible palindromic substring's start position and length, which is represented by "i" and "j" in the code below. Second, check if this substring is palindromic, if so and the length exceeds current max, update max and record this substring. After the traversal, finally we will get a answer.
```cpp
string convert(string s) {
  string ss = s;
  for (int i = 0; i < s.size(); i++) {
    ss[i] = s[s.size()-i-1];
  }
  return ss;
}

int check(string s) {
  string ss = convert(s);
  if (strcmp(s.c_str(), ss.c_str()) == 0) {
    return s.size();
  }
  return 0;
}

string longestPalindrome(string s) {
  int max = 1;
  string maxx = "";
  for (int i = 0; i < s.size(); i++) {
    for (int j = 2; j <= s.size() - i; j++) {
      int tmp = check(s.substr(i, j));
      if (tmp > max) {
        max = tmp;
        maxx = s.substr(i, j);
      }
    }
  }
  if (max == 1) {
    return s.substr(0, 1);
  }
  return maxx;
}
```
