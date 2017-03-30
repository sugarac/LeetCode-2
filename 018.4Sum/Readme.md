### 18. 4Sum  
按照3sum的思路来做4sum，需要n*n*n*log(n)的时间复杂度。  
需要注意必要的剪枝来减少计算量。比如第一层循环
```cpp
for (int h1=0; h1<nums.size(); h1++)
{
   if (nums[h1]*4>target) break;
}
```  
类似的第二层循环
```cpp
for (int h2=0; h2<nums.size(); h2++)
{
   if (nums[h1]+3*nums[h2]>target) break;
}
```    
对于第三层循环
```cpp
int left=h2+1;
if (nums[h1]+nums[h2]+2*nums[left]>target) break;
int right=nums.size()-1;
if (nums[h1]+nums[h2]+2*nums[right]<target) continue;
```    
对于h1(h2)避免重复元素的操作
```cpp
while (h1+1<nums.size() && nums[h1+1]==nums[h1]) h1++;
```