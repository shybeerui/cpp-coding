# priority_queue
## Definition
        template<
            class T,
            class Container = std::vector<T>,
            class Compare = std::less<typename Container::value_type>
        > class priority_queue; 
## Compare function
### 1. greater<T> less<T>
### 2. 四种自定义方法
#### (1). lamda function
        auto cmp = [](pq_element p1, pq_element p2) {  
            return p1.first->val > p2.first->val;  
        };  
        priority_queue<pq_element,vector<pq_element>,decltype(cmp)> pq(cmp);   
#### (2). 重载操作符
        bool operator < (const node &a, const node &b) {
            return a.value < b.value; // 按照value从大到小排列
        } 
        priority_queue<node> q;
#### (3). 自定义比较函数模板结构
        struct cmp{
            bool operator ()(const node &a, const node &b) {
                return a.value > b.value;// 按照value从小到大排列
            }
        };
        priority_queue<node, vector<node>, cmp> q;        
#### (4). 定义友元操作类重载函数（node可能有私有成员所以考虑使用友元）
        struct node{
            int value;
            friend bool operator < (const node &a,const node &b){
                return a.value < b.value;  //按value从大到小排列
            }
        };
        priority_queue<node> q;        
        
## Reference 
https://www.cnblogs.com/flipped/p/5691430.html
