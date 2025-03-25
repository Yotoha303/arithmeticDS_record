
                 if(nums1[j] > nums1[j+1]){
                     int temp = nums1[j];
                     nums1[j] = nums1[j+1];
                     nums1[j+1] = temp;
                 }
             }
        }
		
        //输出数组
		for(int i = 0;i<nums1.length;i++){
			System.out.print(nums1[i]+"\t");
		}
    }
}
```

二代代码：

```
class Solution {
	//逆双指针
    public void merge(int[] nums1, int m, int[] nums2, int n) {
		for (int i = m - 1, j = n - 1, k = m + n - 1; j >= 0; --k) {
            nums1[k] = i >= 0 && nums1[i] > nums2[j] ? nums1[i--] : nums2[j--];
        }    
}
```



#### 27、移除元素

给你一个数组 `nums` 和一个值 `val`，你需要 **[原地](https://baike.baidu.com/item/原地算法)** 移除所有数值等于 `val` 的元素。元素的顺序可能发生改变。然后返回 `nums` 中与 `val` 不同的元素的数量。

假设 `nums` 中不等于 `val` 的元素数量为 `k`，要通过此题，您需要执行以下操作：

- 更改 `nums` 数组，使 `nums` 的前 `k` 个元素包含不等于 `val` 的元素。`nums` 的其余元素和 `nums` 的大小并不重要。
- 返回 `k`。

**示例 1：**

```
输入：nums = [3,2,2,3], val = 3
输出：2, nums = [2,2,_,_]
解释：你的函数函数应该返回 k = 2, 并且 nums 中的前两个元素均为 2。
你在返回的 k 个元素之外留下了什么并不重要（因此它们并不计入评测）。
```

**示例 2：**

```
输入：nums = [0,1,2,2,3,0,4,2], val = 2
输出：5, nums = [0,1,4,0,3,_,_,_]
解释：你的函数应该返回 k = 5，并且 nums 中的前五个元素为 0,0,1,3,4。
注意这五个元素可以任意顺序返回。
你在返回的 k 个元素之外留下了什么并不重要（因此它们并不计入评测）。
```

一代代码

```Java
class Solution {
    public int removeElement(int[] nums, int val) {
        ArrayList<Integer> arr = new ArrayList<>();	
        for(int i = 0;i<nums.length;i++){	//n
            if(nums[i]!=val){
                arr.add(nums[i]);
            }
        }
        return arr.size();
    }
}
```

二代代码（n）

```Java
class Solution {
    public int removeElement(int[] nums, int val) {
        int count = 0;
        for(int i = 0;i<nums.length;i++){
            if(nums[i]!=val){
                nums[count++] = nums[i];
            }
        }
        return count;
    }
}
```

#### 26、删除有序数组中的重复项

给你一个 **非严格递增排列** 的数组 `nums` ，请你**[ 原地](http://baike.baidu.com/item/原地算法)** 删除重复出现的元素，使每个元素 **只出现一次** ，返回删除后数组的新长度。元素的 **相对顺序** 应该保持 **一致** 。然后返回 `nums` 中唯一元素的个数。

考虑 `nums` 的唯一元素的数量为 `k` ，你需要做以下事情确保你的题解可以被通过：

- 更改数组 `nums` ，使 `nums` 的前 `k` 个元素包含唯一元素，并按照它们最初在 `nums` 中出现的顺序排列。`nums` 的其余元素与 `nums` 的大小不重要。
- 返回 `k` 。

**示例 1：**

```
输入：nums = [1,1,2]
输出：2, nums = [1,2,_]
解释：函数应该返回新的长度 2 ，并且原数组 nums 的前两个元素被修改为 1, 2 。不需要考虑数组中超出新长度后面的元素。
```

**示例 2：**

```
输入：nums = [0,0,1,1,1,2,2,3,3,4]
输出：5, nums = [0,1,2,3,4]
解释：函数应该返回新的长度 5 ， 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4 。不需要考虑数组中超出新长度后面的元素。
```

一代代码（n）

```Java
class Solution {
    public int removeDuplicates(int[] nums) {
        int count = 1;
        for(int i = 1;i<nums.length;i++){
            if(nums[i]!=nums[i-1]){
                nums[count++] = nums[i];
            }
        }
        return count;
    }
}
```

