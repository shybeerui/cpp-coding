# priority_queue
## definition
··template<
    class T,
    class Container = std::vector<T>,
    class Compare = std::less<typename Container::value_type>
> class priority_queue;··   
## compare function
### greater<T> less<T>
### 四种自定义方法
#### 1.lamda function
        auto cmp = [](pq_element p1, pq_element p2) {  
            return p1.first->val > p2.first->val;  
        };  
        priority_queue<pq_element,vector<pq_element>,decltype(cmp)> pq(cmp);   
