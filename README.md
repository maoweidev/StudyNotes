# StudyNotes
# 笔记



##### 8月10日

1. **算法**

   + 题目：力扣 88.合并两个有序数组，给你两个按 **非递减顺序** 排列的整数数组 `nums1` 和 `nums2`，另有两个整数 `m` 和 `n` ，分别表示 `nums1` 和 `nums2` 中的元素数目。请你 **合并** `nums2` 到 `nums1` 中，使合并后的数组同样按 **非递减顺序** 排列。

   - 思路：一开始想的是先将nums2数组中所有的元素全部放到nums1数组空余的位置，然后再将nums1数组排序，实现代码如下：

     ```
     class Solution {
         public void merge(int[] nums1, int m, int[] nums2, int n) {
             for(int i=0; i<n; i++){
                 nums1[m+i] = nums2[i];
             }
     
             for(int i=0; i<m+n; i++){
                 for(int j=0; j<m+n-i-1; j++) {
                     if(nums1[j]>nums1[j+1]){
                         int temp=nums1[j];
                         nums1[j]=nums1[j+1];
                         nums1[j+1]=temp;
                     }
                 }
             }
         }
     }
     ```

     代码提交截图如下：

     ![image-20230810222859959](C:\Users\maowei\AppData\Roaming\Typora\typora-user-images\image-20230810222859959.png)

​				可以看到这种方法的时间性能不佳，另一种更好的方法是双指针。为nums1数组和nums2数组分别定义一个指针为p1、p2。

​			比较p1和p2指针哪个指向的元素最小，就将较小的那个元素保存，并将相应的指针加一。实现代码如下：

```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p1 = 0, p2 = 0;
        int cur;
        int[] sorted = new int[m + n];

        while (p1 < m || p2 < n) {
            if (p1 == m) {
                cur = nums2[p2++];
            } else if (p2 == n) {
                cur = nums1[p1++];
            } else if (nums1[p1] < nums2[p2]) {
                cur = nums1[p1++];
            } else {
                cur = nums2[p2++];
            }
            sorted[p1+p2-1] = cur;
        }

        for (int i = 0; i < m + n; i++) {
            nums1[i] = sorted[i];
        }
    }
}
```

代码提交截图如下：

![image-20230810223653139](C:\Users\maowei\AppData\Roaming\Typora\typora-user-images\image-20230810223653139.png)



2. **Java**

   - <font color=Blue>包</font>

   包的作用：包就是文件夹，用来管理各种不同功能的Java类。

   包的书写规则：公司域名反写+包的作用，全英文小写，如com.maowei.learn。

   全类名：包名+类名。

   导包： 使用同一个类中的包时，无需导包；

   ​			使用Java.lang中的包时，无需导包；

   ​			同时使用两个包中的同类名，需要导包。

   - <font color=Blue> final</font>

   final修饰的类：最终类，不能被继承；

   final修饰的方法：最终方法，不能被重写；

   final修饰的变量：常量，只能被赋值一次。

   

   

   







