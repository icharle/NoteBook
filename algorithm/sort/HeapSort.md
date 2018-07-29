# 堆排序

>原理：首先将待排序的记录序列构造成一个堆，此时，选出了堆中所有记录的最大者即堆顶记录，然后将它从堆中移走（通常将堆顶记录和堆中最后一个记录交换），并将剩余的记录再调整成堆，这样又找出了次大的记录，以此类推，直到堆中只有一个记录为止。

>时间复杂度：平均情况为:**O(n㏒n)**

>适用范围：堆排序属于**不稳定排序**，采用**减治法**策略。

## 代码实现

```
<?php

class Sort
{
    /**
     * @param $arr 待排序的无序数组
     */
    public function HeapSort(&$arr)
    {
        $len = count($arr);

        //初始化堆(构建一个大根堆)
        for ($i = ($len / 2) - 1; $i >= 0; $i--) {
            $this->SiftHeap($arr, $i, $len);
        }

        //交换堆顶与堆底元素 并且重新整理堆
        for ($i = $len - 1; $i >= 0; $i--) {
            list($arr[0], $arr[$i]) = array($arr[$i], $arr[0]);

            $this->SiftHeap($arr, 0, $i);
        }

    }

    /**
     * @param $arr  待排序的无序数组
     * @param $s    开始位置
     * @param $n    无序数组长度
     */
    public function SiftHeap(&$arr, $s, $n)
    {
        for ($k = $s * 2 + 1; $k < $n; $k = $k * 2 + 1) {

            if ($k != $n - 1 && $arr[$k] < $arr[$k + 1]) {          //比较节点中左孩子跟右孩子大小
                $k++;
            }

            if ($arr[$s] >= $arr[$k]) {                             //比较节点跟孩子节点大小  满足大根堆排序
                break;
            }

            list($arr[$s], $arr[$k]) = array($arr[$k], $arr[$s]);   //与子节点交换值
            $s = $k;

        }
    }
}

$a = new Sort();
$arr = array('47', '33', '35', '2', '18', '71', '26', '13');
$a->HeapSort($arr);
var_dump($arr);

?>

```


