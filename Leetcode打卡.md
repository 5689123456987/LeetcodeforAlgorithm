#### **1**  给你一个字符串 s，找到 s 中最长的回文子串

 

示例 1：

输入：s = "babad"
输出："bab"
解释："aba" 同样是符合题意的答案。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-palindromic-substring
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```c++
class Solution {
public:
    string longestPalindrome(string s) {
        //暴力解法
        // short len = s.length();
        // // cout<<len;
        // short max = 0;
        // short maxleft = 0;
        // short maxright = 0;
        // for(short i = 0; i < len;i++){
        //     for(short j = i;j < len; j++){
        //         if(validlongestPalindrome(s,i,j) && (j-i)>=max){
        //             max = j - i + 1;
        //             maxleft = i;
        //             maxright = j;
        //         }       
        //     }
        // }
        // cout<<maxleft<<maxright;
        // // cout<<max;
        // return s.substr(maxleft,maxright-maxleft+1);

		if (s.length() < 1)
		{
			return "";
		}
		short start = 0, end = 0;
		for (short i = 0; i < s.length(); i++)
		{
			short len1 = expandAroundCenter(s, i, i);//一个元素为中心
			short len2 = expandAroundCenter(s, i, i + 1);//两个元素为中心
			short len = max(len1, len2);
			if (len > end - start)
			{
				start = i - (len - 1) / 2;
				end = i + len / 2;
			}
		}
		return s.substr(start, end - start + 1);
	}

	short expandAroundCenter(string &s, short left, short right)
	{
		short L = left, R = right;
		while (L >= 0 && R < s.length() && s[L] == s[R])
		{// 计算以left和right为中心的回文串长度
			L--;
			R++;
		}
		return R - L - 1;
	}
    bool validlongestPalindrome(string &s,short i,short j){
        while(i<j){
            if(s[i]!=s[j])
                return false;
            i++;
            j--;
        }
        return true;
    }
};
```

