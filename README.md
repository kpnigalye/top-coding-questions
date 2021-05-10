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
```
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

