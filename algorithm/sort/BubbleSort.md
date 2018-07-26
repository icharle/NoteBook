# 冒泡排序

>原理：相邻两个数中若不是正序则交换位置，使其按照顺序排列。

>时间复杂度：最好情况(正序):**O(n)**     最坏情况(逆序):**O(n∧2)**

>适用范围：插入排序属于**稳定排序**，采用**蛮力法**策略，使用于数据**规模较小**的数据。

## 代码实现

```
<?php

class Sort
{
    /**
     * 冒泡排序
     * @param $arr  待排序数组
     * @param $n    待排序数组长度
     * @return mixed    已排序数组
     */
    public function BubbleSort($arr)
    {
        $n = count($arr);
        for ($i=0; $i < $n; $i++) {
            $flag = false;          //标志位
            for ($j=0; $j < $n-$i ; $j++) {
                if ($arr[$j+1] < $arr[$j]) {
                    $flag = true;
                    $temp = $arr[$j+1];
                    $arr[$j+1] = $arr[$j];
                    $arr[$j] = $temp;
                }
            }
            if(!flag) break;        //未进行交换，排序直接结束
        }
        return $arr;
    }
}

$a = new Sort();
$res = $a->BubbleSort(array('3','1','6','5','2'));
var_dump($res);

?>
```



