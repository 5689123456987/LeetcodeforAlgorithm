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



#### 2 打家劫舍

你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

给定一个代表每个房屋存放金额的非负整数数组，计算你 不触动警报装置的情况下 ，一夜之内能够偷窃到的最高金额。

 

示例 1：

输入：[1,2,3,1]
输出：4
解释：偷窃 1 号房屋 (金额 = 1) ，然后偷窃 3 号房屋 (金额 = 3)。
     偷窃到的最高金额 = 1 + 3 = 4 。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/house-robber
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```c++
class Solution {
public:
int rob(vector<int>& nums) {
int n=size(nums);
if(n==0) return 0;
if(n==1) return nums[0];
int first=nums[0];
int second=max(nums[0],nums[1]);
for(int i=2;i<n;i++)
{
    int temp=second;
second=max(second,first+nums[i]);
first=temp;
}
return second;
}
};
```

