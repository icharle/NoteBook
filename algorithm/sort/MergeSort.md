# 归并排序

>原理：二路归并

>时间复杂度：平均情况:**O(n㏒2n)**

>适用范围：归并排序属于**稳定排序**，采用**分治法**策略。

## 代码实现

```
<?php

class Sort
{
    /**
     * @param $arr  待排序数组
     * @return mixed    已排序数组
     */
    public function MergeSort($arr)
    {
        $len = count($arr);     //统计字符串长度
        $res = array();
        $this->Msort($arr, $res, 0, $len - 1);
        return $res;
    }

    /**
     * @param $arr  待排序数组
     * @param $res  排序好数组
     * @param $s    起始偏移量
     * @param $t    结束偏移量
     */
    public function Msort(&$arr, &$res, $s, $t)
    {
        if ($s == $t) {
            $res[$s] = $arr[$t];                //当只有一个元素直接输出、大于一个元素，拆分成左右两部分，分别进行归并排序
        } else {
            $mid = intval(($s + $t) / 2);           //划分
            $temp = array();
            $this->Msort($arr, $temp, $s, $mid);            //前半部分子序列
            $this->Msort($arr, $temp, $mid + 1, $t);     //后半部分子序列
            $this->Merge($temp, $res, $s, $mid, $t);            //合并两个子序列
        }
    }

    /**
     * @param $temp 待排序数组
     * @param $res  排序好数组
     * @param $s    起始偏移量
     * @param $mid  中间偏移量
     * @param $t    结束偏移量
     * 相邻子序列$temp[$s]~$temp[$mid]和$temp[$mid+1]~$temp[$t]合并为一个子序列$res[$s]~$res[$t]
     */
    public function Merge(&$temp, &$res, $s, $mid, $t)
    {
        $i = $s;
        $j = $mid + 1;
        $k = $s;
        //取$temp[$i]和$temp[$j]中较小者放入$res[$k]
        while ($i <= $mid && $j <= $t) {
            if ($temp[$i] <= $temp[$j]) {
                $res[$k++] = $temp[$i++];
            } else {
                $res[$k++] = $temp[$j++];
            }
        }
        //若第一个子序列没处理完，则进行收尾处理
        while ($i <= $mid) {
            $res[$k++] = $temp[$i++];
        }
        //若第二个子序列没处理完，则进行收尾处理
        while ($j <= $t) {
            $res[$k++] = $temp[$j++];
        }
    }
}

$a = new Sort();
$res = $a->MergeSort(array('3', '1', '6', '5', '2'));
var_dump($res);

?>

```

