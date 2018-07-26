# 选择排序

>原理：每一趟从待排序的记录中选出最小的记录，顺序的放在已排好序的子序列的最后，直到全部记录排序完毕。

>时间复杂度：平均情况为:**O(n∧2)**

>适用范围：插入排序属于**不稳定排序**，采用**蛮力法**策略，适用于数据**规模较大**的数据。

## 代码实现

```
<?php

class Sort
{
    /**
     * @param $arr  待排序数组
     * @return mixed    已排序数组
     */
    public function SelectSort($arr)
    {
        $num = count($arr);     
        for ($i = 0; $i < $num - 1; $i++) {

            $minpos = $i;         //设置默认第一个为最小值
            for ($j = $i + 1; $j < $num; $j++) {
                if ($arr[$j] < $arr[$minpos]) {
                    $minpos = $j;        //更换最小位置
                }
            }
            if ($minpos != $i) {                //交换最小值
                $temp = $arr[$minpos];
                $arr[$minpos] = $arr[$i];
                $arr[$i] = $temp;
            }

        }
        return $arr;
    }
}

$a = new Sort();
$res = $a->SelectSort(array('3', '1', '6', '5', '2'));
var_dump($res);

?>
```


