 Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(h)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
int count(Node*root){
    if(root==NULL)
        return 0;
    
    return 1+count(root->left)+count(root->right);
}
int recur(Node*root,int i,int target,int &val){
    if(root==NULL)
        return i;
    
    i=recur(root->left,i,target,val);
    i++;
    if(i==target)
        val=root->data;
    i=recur(root->right,i,target,val);
    
    return i;
}

float findMedian(struct Node *root){
      //Code here
      int n=count(root);
      if(n%2==0)
      {
          int mid1=0,mid2=0;
          recur(root,0,n/2,mid1);
          recur(root,0,1+n/2,mid2);
          return (float)(mid1+mid2)/2.0;
      }else{
          int mid=0;
          recur(root,0,1+n/2,mid);
          return mid;
      }

}
```
