第一周

### 简单：

* 用 add first 或 add last 这套新的 API 改写 Deque 的代码
* 分析 Queue 和 Priority Queue 的源码
* [删除排序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)（Facebook、字节跳动、微软在半年内面试中考过）
* [旋转数组](https://leetcode-cn.com/problems/rotate-array/)（微软、亚马逊、PayPal 在半年内面试中考过）
* [合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)（亚马逊、字节跳动在半年内面试常考）
* [合并两个有序数组](https://leetcode-cn.com/problems/merge-sorted-array/)（Facebook 在半年内面试常考）
* [两数之和](https://leetcode-cn.com/problems/two-sum/)（亚马逊、字节跳动、谷歌、Facebook、苹果、微软在半年内面试中高频常考）
* [移动零](https://leetcode-cn.com/problems/move-zeroes/)（Facebook、亚马逊、苹果在半年内面试中考过）
* [加一](https://leetcode-cn.com/problems/plus-one/)（谷歌、字节跳动、Facebook 在半年内面试中考过）
### 中等：

* [设计循环双端队列](https://leetcode.com/problems/design-circular-deque)（Facebook 在 1 年内面试中考过）
### 困难：

* [接雨水](https://leetcode.com/problems/trapping-rain-water/)（亚马逊、字节跳动、高盛集团、Facebook 在半年内面试常考）

---


1、用 add first 或 add last 这套新的 API 改写 Deque 的代码

2、分析 Queue 和 Priority Queue 的源码

3、[删除排序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)（Facebook、字节跳动、微软在半年内面试中考过）

双指针：

关键点

1、使用 i 和 j 两个指针遍历数组 ，j 在 i 前寻找不重复元素

2、发现不重复元素往前移动至第一个重复元素位置

3、最终数组长度为指针 i 走过的路程长度

```plain
public int removeDuplicates(int[] nums) {
    if (nums == null || nums.length <= 0) {
        return 0;
    }
    int i = 0;
    int j = 1;
    while (j < nums.length) {
        if (nums[i] != nums[j]) {
            nums[i + 1] = nums[j];
            i++;
        }
        j++;
    }
    return i + 1;
}
```
4、[旋转数组](https://leetcode-cn.com/problems/rotate-array/)（微软、亚马逊、PayPal 在半年内面试中考过）
5、[合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)（亚马逊、字节跳动在半年内面试常考）

解题思路：

递归找到两个链表中相对较小的结点

递归三要素：

终止条件：l1 、l2 结点为null

递归体： 找到相对较小的一个结点

返回值：将找到的结点返回

```plain
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    if (l1 == null)
        return l2;
    if (l2 == null)
        return l1;
    ListNode head = new ListNode();
    if (l1.val < l2.val) {
        head.val = l1.val;
        head.next = mergeTwoLists(l1.next, l2);
    } else {
        head.val = l2.val;
        head.next = mergeTwoLists(l2.next, l1);
    }
    return head;
}
```
6、[合并两个有序数组](https://leetcode-cn.com/problems/merge-sorted-array/)（Facebook 在半年内面试常考）
7、[两数之和](https://leetcode-cn.com/problems/two-sum/)（亚马逊、字节跳动、谷歌、Facebook、苹果、微软在半年内面试中高频常考）

暴力法：枚举所有两个数相加的和

```plain
public int[] twoSum(int[] nums, int target) {
    for (int i = 0; i < nums.length - 1; i++) {
        for (int j = i + 1; j < nums.length; j++) {
            if (target == (nums[i] + nums[j])) {
                return new int[]{i, j};
            }
        }
    }
    return new int[0];
}
```
哈希映射法：
```plain
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (map.containsKey(target - nums[i])) {
            return new int[]{map.get(target - nums[i]), i};
        }
        map.put(nums[i], i);
    }
    return new int[0];
}
```
8、[移动零](https://leetcode-cn.com/problems/move-zeroes/)（Facebook、亚马逊、苹果在半年内面试中考过）
解题思路：

第一层循环：将所有非零元素移动到数组开头

第二层循环：将剩余元素皆赋值为0

```plain
public void moveZeroes(int[] nums) {
    int p = 0;
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != 0) {
            nums[p++] = nums[i];
        }
    }
    for (int j = p; j < nums.length; j++) {
        nums[j] = 0;
    }
}
```
9、[加一](https://leetcode-cn.com/problems/plus-one/)（谷歌、字节跳动、Facebook 在半年内面试中考过）
10、[设计循环双端队列](https://leetcode.com/problems/design-circular-deque)（Facebook 在 1 年内面试中考过）

11、[接雨水](https://leetcode.com/problems/trapping-rain-water/)（亚马逊、字节跳动、高盛集团、Facebook 在半年内面试常考）

