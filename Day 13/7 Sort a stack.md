# [Sort a stack](https://www.codingninjas.com/codestudio/problems/sort-a-stack_985275?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website&leftPanelTab=0)

### Code ||

``` .cpp
void sortedInsert(stack<int> &stack,int num){
    if(stack.empty() || (stack.top()<num && !stack.empty())){
        stack.push(num);
        return;
    }
    
    int x=stack.top();
    stack.pop();
    sortedInsert(stack,num);
    stack.push(x);
    
    
}
void sortStack(stack<int> &stack)
{
    // Write your code here
    if(stack.empty())
        return;
    
    int num=stack.top();
    stack.pop();
    
    sortStack(stack);
    sortedInsert(stack,num);
        
    
}
```
```
TC:- O(n^2)
SC:- O(n)
```
