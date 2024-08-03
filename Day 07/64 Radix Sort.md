# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n*d) where d is number digits in maximum number
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n+d)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
void countSort(int arr[], int n, int exp)
{

    int output[n];
    int i,count[10]={0};

    for(i=0;i<n;i++)
        count[(arr[i]/exp)%10]++;

    for(i=1;i<10;i++)
        count[i]+=count[i-1];

    for(i=n-1;i>=0;i--){
        output[count[(arr[i]/exp)% 10]-1]=arr[i];
        count[(arr[i]/exp)%10]--;
    }

    for(i=0;i<n;i++)
        arr[i]=output[i];
}

void radixSort(int arr[], int n) 
{ 
    // code here
    int maxi=*max_element(arr,arr+n);

    for(int i=1;maxi/i>0;i*=10){
        countSort(arr,n,i);
    }
} 
```