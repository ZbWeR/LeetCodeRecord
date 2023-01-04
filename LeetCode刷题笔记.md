## LeetCode刷题笔记

### 二分查找模板

```cpp
int l,r,mid;
while(l<=r){
    mid = (l+r)/2;
    // 如果符合条件,check返回true
    if(check(mid)) l = mid+1;
    else r = mid-1;
}
return r;
```

关于返回值为`r`的解释: $mid$ 满足条件说明比 $mid$ 小的都满足,因此我们要把 $l$ 右移为`mid+1`去找更大的临界点. 那么 $l$ 最后的位置再减一,就一定是最后符合条件的 $mid$.而这个位置恰巧就是$r$,因为while停止的条件是 `r<l` ,即 `r=l-1=mid`, 故返回 r.