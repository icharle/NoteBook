# 快速排序

>原理：选择一个记录作为轴值，以轴值为基准，将整个序列划分为两个子序列，前一个子序列的值均小于等于轴值，后一个子序列的值均大于等于轴值，整个排序过程采用递归思想。

>时间复杂度：最好情况:**O(n㏒2n)**     最坏情况:**O(n∧2)**

>适用范围：快速排序属于**不稳定排序**，采用**分治法**策略。

## 代码实现

```
<?php

class Sort
{
    /**
     * @param $arr      待排序数组
     * @param $left     左偏移量
     * @param $right    右偏移量
     * @return mixed
     * 一次划分
     */
    public function Partition(&$arr, $left, $right)
    {
        while ($left < $right) {
            //后面往前扫描(找到比轴值小的进行交换)
            while ($left < $right && $arr[$left] <= $arr[$right]) {
                $right--;
            }
            if ($left < $right) {
                $temp = $arr[$left];
                $arr[$left] = $arr[$right];
                $arr[$right] = $temp;
                $left++;
            }
            //前面往后扫描(找到比轴值大的进行交换)
            while ($left < $right && $arr[$left] <= $arr[$right]) {
                $left++;
            }
            if ($left < $right) {
                $temp = $arr[$left];
                $arr[$left] = $arr[$right];
                $arr[$right] = $temp;
                $right--;
            }
        }
        return $left;        //返回轴值的位置
    }

    /**
     * @param $arr      待排序数组
     * @param $first    左偏移量
     * @param $end      右偏移量
     * 递归调用
     */
    public function QSort(&$arr, $first, $end)
    {
        if ($first < $end) {
            $pivot = $this->Partition($arr, $first, $end);
            $this->QSort($arr, $first, $pivot - 1);
            $this->QSort($arr, $pivot + 1, $end);
        }
    }

    /**
     * @param $arr      待排序数组
     */
    public function QuickSort(&$arr)
    {
        $low = 0;
        $high = count($arr) - 1;
        $this->QSort($arr, $low, $high);
    }
}

$a = new Sort();
$arr = array('3', '1', '6', '5', '2');
$a->Quicksort($arr);
var_dump($arr);

?>

```

