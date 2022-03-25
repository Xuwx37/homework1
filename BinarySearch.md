# 二分搜索算法
二分搜索算法是一种适用于大量数据查找的算法，但其有两个要求：第一是数列是**有序数列**，第二是数列使用**顺序存储**结构。每次将待找数据与中间的值进行比较，根据比较的结果可以直接舍去一半的值，直至全部找完（可能未找到数据）或者找到数据为止。
## 二分搜索算法原理
假设在 [*begin*,*end*] 范围内搜索某个元素 *v* ,设中间位置 *mid* = (*begin*+*end*)/2，该中间位置对应的值为*m*：
- 若*v* < *m*,则在 [*begin*,*mid*] 的范围内二分搜索
- 若*v* > *m*,则在 [*mid+1*,*end*] 的范围内二分搜索
- 若*v* = *m*,则直接返回*mid*

算法实现原理图如下：  
![原理图](theory.png#pic_center)  
为了解二分搜索算法的原理，也可以点击[二分搜索算法动画讲解](https://www.bilibili.com/video/BV1wy4y1k76F?spm_id_from=333.337.search-card.all.click)，其为我们进行了形象生动的讲解。
## 二分搜索算法实例
在如下升序序列中查找元素31

![示例](http://c.biancheng.net/uploads/allimg/210820/2-210R0143956357.gif)  
1.如下图1所示，所有元素的位置用0~9表示，则中间元素的位置 mid=(0+9)/2=4，其对应的中间元素的值为27<31，因此在[5,9]的范围内进行二分搜索  
![图1](num2.gif)  
2.如下图2所示，在[5,9]的范围内，中间元素的位置 mid=(5+9)/2=7，其对应的中间元素的值为35>31，因此在[5,6]的范围内进行二分搜索    
![图2](num3.gif)  
3.如下图3所示，在[5,6]的范围内，中间元素的位置 mid=(5+6)/2=5，其对应的中间元素的值就是31，成功找到目标元素。  
![图3](num4.gif)
## 二分搜索算法代码实现
用二分搜索算法在[10,14,19,26,27,31,33,35,42,44]升序序列中查找元素31的Java程序如下所示：
```
public class Demo {
    // 实现二分搜索算法，ele 表示要查找的目标元素，[p,q] 指定查找区域
    public static int binary_search(int[] arr, int p, int q, int ele) {
        // 如果[p,q] 不存在，返回 -1
        if (p > q) {
            return -1;
        }
        // 找到中间元素所在的位置
        int mid = (p + q) / 2;
        // 递归的出口
        if (ele == arr[mid]) {
            return mid;
        }
        // 比较 ele 和 arr[mid] 的值，缩小 ele 可能存在的区域
        if (ele < arr[mid]) {
            // 新的搜索区域为 [p,mid-1]
            return binary_search(arr, p, mid - 1, ele);
        } else {
            // 新的搜索区域为 [mid+1,q]
            return binary_search(arr, mid + 1, q, ele);
        }
    }

    public static void main(String[] args) {
        int[] arr = new int[] { 10, 14, 19, 26, 27, 31, 33, 35, 42, 44 };
        // 输出目标元素 31 所在位置的下标
        int add = binary_search(arr, 0, 9, 31);
        System.out.print(add);
    }
}
```











