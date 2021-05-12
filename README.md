# Top Coding Questions
Top interview coding questions and my solutions

1. Find the missing number in the array ([solution](https://codesandbox.io/s/find-missing-number-in-an-array-dsdrc?file=/src/index.js))
```javascript
// time complexity is O(n)
const findMissingNumber = (arr) => {
  const length = arr.length;
  let sum = 0;

  for (let i = 1; i <= length + 1; i++) {
    sum += i;
  }

  for (let i = 0; i < length; i++) {
    sum -= arr[i];
  }

  console.log(`Missing number is ${sum}`);
};

findMissingNumber([3, 7, 6, 2, 8, 4, 5]);
```

2. Determine if the sum of two integers is equal to the given value ([solution](https://codesandbox.io/s/find-sum-of-two-cpl9f))
```javascript
// time complexity O(n)
// space complexity O(n)
function findSumOfTwo(nums, sum) {
  if (nums.length > 0 || sum === 0) {
    let dict = {};
    for (let i = 0; i < nums.length; i++) {
      dict[nums[i]] = sum - nums[i];
    }

    for (let key in dict) {
      if (nums.includes(Number(key)) && nums.includes(dict[key])) {
        return true;
      }
    }
  }
  return false;
}

console.log(findSumOfTwo([5, 2, 8, 4], 13));
```

3. Merge two sorted lists
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/merge-two-sorted-lists/)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, l1, l2):
        head = cur = ListNode(0)
        while l1 and l2:
            if l1.val <= l2.val:
                cur.next = l1
                l1 = l1.next
            else:
                cur.next = l2
                l2 = l2.next
            cur = cur.next
        cur.next = l1 or l2
        return head.next
```

4. Reverse words in a string
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/reverse-words-in-a-string/)
```python
def reverseWords(s):
    word = ''
    words = []
    
    for letter in s:
        if letter == ' ':
            if word != '':
                words.append(word)
                word = ''
        else:
            word = word + letter

    if word != '':
        words.append(word)

    s = ''
    while len(words) > 0:
        s = s + words.pop()
        if len(words) > 0:
            s = s + ' '

    return s
```

5. Find first non-recurring character in a string 
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/first-unique-character-in-a-string/)
```csharp
public class Solution {
    public int FirstUniqChar(string s) {
      if(s.Length < 1 || s.Length > Math.Pow(10, 5))
        return -1;
      else {
        // char -> key 
        // position -> value
        Dictionary<char, int> dict = new Dictionary<char, int>();
        for(int i = 0; i < s.Length; i++) {
          if(!dict.ContainsKey(s[i])) {
            dict[s[i]] = i;
          } else {
            dict[s[i]] = -1;  // duplicate
          }
        }
        
        int minIndex = Int32.MaxValue;
        foreach(var item in dict) {
          if (item.Value != -1 && item.Value < minIndex) {
            minIndex = item.Value;
          }
        }
        
        return minIndex == Int32.MaxValue ? -1 : minIndex;
      }
    }
}
```

6. Single Number
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/single-number/)

```csharp
public class Solution {
    public int SingleNumber(int[] nums) {
      // number-> key
      // occurance -> value
      Dictionary<int, int> dict = new Dictionary<int, int>();
      int unique = -1;
      
      for(int i=0; i <nums.Length; i++) {
        if(dict.ContainsKey(nums[i])) {
          dict[nums[i]] += 1;
        } else {
          dict[nums[i]] = 1;
        }
      }
      
      foreach(var item in dict) {
        if(item.Value == 1) {
          unique = item.Key;
          break;
        }
      }
      return unique;
    }
}
```
7. Power of Two
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/power-of-two/)

```csharp
public class Solution {
    public bool IsPowerOfTwo(int n) {
      long num = 1;
      while(num < n) {
        num *= 2;
      }
      
      return n == num;
    }
}
```

8. Robort return to Origin
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/robot-return-to-origin/)
```csharp
public class Solution {
    public bool JudgeCircle(string moves) {
      if( moves.Length < 1 && (moves.Length > 2 * Math.Pow(10, 4)))
        return false;
      
      int x = 0, y = 0;
      for(int i = 0; i < moves.Length; i++) {
        switch(moves[i]) {
          case 'L': x -= 1;
            break;
          case 'R': x += 1;
            break;
          case 'U': y += 1;
            break;
          case 'D': y -= 1;
            break;
          default: break;
        }
      }
      return x == 0 && y ==0;
    }
}
```

9. Missing Number
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/missing-number/)
```csharp
public class Solution {
    public int MissingNumber(int[] nums) {
      int len = nums.Length;
      int expectedSum = (len * (len + 1))/2;
      int sum = 0;
      for(int i =0; i<len;i++) {
        sum += nums[i];
      }
      return expectedSum - sum;
    }
}
```

10. Best time to buy and Sell Stock II
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)
```csharp
public class Solution {
    public int MaxProfit(int[] prices) {
      if(prices.Length == 0 || prices == null) return 0;
      
      int profit = 0;
      for(int i = 0; i< prices.Length - 1; i++) {
        if(prices[i + 1] > prices[i]) {
          profit += prices[i+1] - prices [i];
        }
      }
      return profit;
    }
}
```

11. Path Sum
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/path-sum/)
```csharp
public class Solution {
    public bool HasPathSum(TreeNode root, int targetSum) {
      if(root == null) {
        return false;
      } else if (root.left == null && root.right == null && targetSum - root.val == 0) {
        return true;
      } else {
        return HasPathSum(root.left, targetSum - root.val) || HasPathSum(root.right, targetSum - root.val);
      }
    }
}
```

12. Remove Element
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/remove-element/)
```csharp
public class Solution {
    public int RemoveElement(int[] nums, int val) {
      int start = 0, end = nums.Length -1;
      int count = 0;
      while(start <= end) {
        if(nums[end] == val) {
          end --;
          count++;
        }
        else if(nums[start] == val) {
          nums[start] = nums[end];
          nums[end] = val;
          start++;
          end--;
          count++;
        } else {
          start++;
        }
      }
      return nums.Length - count;
    }
}
```

13. Climbing Stairs
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/climbing-stairs/)
```csharp
public class Solution {
    public int ClimbStairs(int n) {
      int[] dp = new int[n+1];
      dp[0] = 1;
      dp[1] = 1;
      
      for(int i = 2; i<= n; i++) {
        dp[i] = dp[i-1] + dp[i-2];
      }
      
      return dp[n];
    }
}
```
14. Lowest Common Ancestor 
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
```csharp
public class Solution {
    public TreeNode LowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(p.val < root.val && q.val < root.val) {
          return LowestCommonAncestor(root.left, p, q);
        } else if (p.val > root.val && q.val > root.val) {
          return LowestCommonAncestor(root.right, p, q); 
        } else {
          return root;
        }
    }
}
```
15. Jewels and Stones
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/jewels-and-stones/)
```csharp
public class Solution {
    public int NumJewelsInStones(string jewels, string stones) {
      if(stones.Length == 0 || stones == null) return 0;
      
      Dictionary<char, int> dict = new Dictionary<char, int>();
      int result = 0;
      
      foreach(char stone in stones) {
        if(dict.ContainsKey(stone)) {
          dict[stone] += 1;
        } else {
          dict[stone] = 1;
        }
      }
      
      foreach(char jewel in jewels) {
        if(dict.ContainsKey(jewel)) {
          result += dict[jewel];
        }
      }
      
      return result;
    }
}
```

16. Container with Most Water
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/container-with-most-water/)
```csharp
/*
  O(n^2) solution 
  
  public class Solution {
      public int MaxArea(int[] height) {
        int max = Int32.MinValue;
        for(int i=0; i < height.Length; i++) {
          for(int j=i+1; j < height.Length; j++) {
            int area = Math.Min(height[i], height[j]) * (j-i);
            max = Math.Max(area, max);
          }  
        }
        return max;
      }
  }
*/

public class Solution {
    public int MaxArea(int[] height) {
      int max = Int32.MinValue;
      int start = 0, end = height.Length -1;
      while(start < end) {
        int min = Math.Min(height[start], height[end]);
        max = Math.Max(max, min * (end - start));
        if(height[start] < height[end]) {
          start++;
        } else {
          end--;
        }
      }
      return max;
    }
}
```
17. Reverse a Linked List
- Here is the link to the problem on [leetcode](https://leetcode.com/problems/reverse-linked-list/)
```csharp
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
 * }
 */
public class Solution {
    public ListNode ReverseList(ListNode head) {
      if(head == null) return head;
      
      ListNode temp, prev = null;
      ListNode current = head;
      while(current != null) {
        temp = current.next;
        current.next = prev;
        prev = current;
        current = temp;
      }
      return prev;
    }
}
```
