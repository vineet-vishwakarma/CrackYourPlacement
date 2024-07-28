# Code
```
class Solution{
  public:
  
    //Function to find starting point where the truck can start to get through
    //the complete circle without exhausting its petrol in between.
    int tour(petrolPump p[],int n)
    {
       //Your code here
       int petrol=0;
       int distance=0;
       
       for(int i=0;i<n;i++){
           petrol+=p[i].petrol;
           distance+=p[i].distance;
       }
       if(petrol<distance){
           return -1;
       }
       
       int total=0;
       int index=0;
       
       for(int i=0;i<n;i++){
            total+=p[i].petrol-p[i].distance;
            if(total<0){
                index=i+1;
                total=0;
            }
       }
       
       return index;
    }
};
```