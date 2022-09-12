[Missing Number](https://leetcode.com/problems/missing-number/)

#### Method:1 XOR
* Let x be the desired output elements.
* Calculate XOR of all the array elements.
  - xor1 = arr[0]^arr[1]^arr[2]…..arr[n-1]
* XOR the result with all numbers from 1 to n
  - xor1 = xor1^1^2^…..^n
* In the result xor1, all elements would nullify each other except x

```java
public int missingNumber(int[] nums) { //xor
    int res = nums.length;
    for(int i=0; i<nums.length; i++){
        res ^= i;
        res ^= nums[i];
    }
    return res;
}
```

#### Method:2 SUM
```java
public int missingNumber(int[] nums) { //sum
    int len = nums.length;
    int sum = (0+len)*(len+1)/2;
    for(int i=0; i<len; i++)
        sum-=nums[i];
    return sum;
}
```


#### Method:3 Binary Search
```java
public int missingNumber(int[] nums) { //binary search
    Arrays.sort(nums);
    int left = 0, right = nums.length, mid= (left + right)/2;
    while(left<right){
        mid = (left + right)/2;
        if(nums[mid]>mid) right = mid;
        else left = mid+1;
    }
    return left;
}
```

Summary: If the array is in order, prefer Binary Search method. Otherwise, the XOR method is better.