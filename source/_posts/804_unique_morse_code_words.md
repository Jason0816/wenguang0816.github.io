---
title: LeetCode刷题：804.Unique Morse Code Words
date: 2019-02-24 13:21:00
categories: LeetCode
tags:
  - LeetCode
---
#### [804\. Unique Morse Code Words](https://leetcode-cn.com/problems/unique-morse-code-words/)
International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows: `"a"` maps to `".-"`, `"b"`maps to `"-..."`, `"c"` maps to `"-.-."`, and so on.
For convenience, the full table for the 26 letters of the English alphabet is given below:
```
[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
```
Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cab" can be written as "-.-..--...", (which is the concatenation "-.-." + "-..." + ".-"). We'll call such a concatenation, the transformation of a word.
Return the number of different transformations among all words we have.

**Example:**

**Input:** `words = ["gin", "zen", "gig", "msg"]`

**Output:** `2`

**Explanation:** 
The transformation of each word is:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."
There are 2 different transformations, "--...-." and "--...--.".

**Note:**
*   The length of `words` will be at most `100`.
*   Each `words[i]` will have length in range `[1, 12]`.
*   `words[i]` will only consist of lowercase letters.
##### 解题思路：
将words中word的字母逐个转换为morsecode，并存入临时string，之后将其插入到无序容器`unordered_set<string> result;`中，然后获取不同元素的数量。
##### 解答：
```
class Solution {
public:
    int uniqueMorseRepresentations(vector<string>& words) {
        unordered_set<string> result;
        //vector<string>morseWords;
        vector<string> morseCode{".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."};
        for(auto word = words.begin(); word != words.end(); ++word)
        {
            string tmp = "";
            for(auto letter : *word)
            {
                tmp += morseCode[letter - 'a'];
            }
            result.insert(tmp);
        }
        return result.size();
    }
};
```