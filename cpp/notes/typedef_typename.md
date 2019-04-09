# C++ typedef typename

先看一段代码：

```c++
// T = ngx_list_t, ngx_array_t, ngx_pool_t, ...
template<typename T>
class NgxWrapper
{
public:
    typedef typename ::boost::remove_pointer<T>::type wrapped_type;

    typedef wrapped_type* pointer_type;
    typedef wrapped_type& reference_type;
private:
    pointer_type m_ptr = nullptr;
```

正常自定义类型的别名应该类似 `typedef int my_int` ，为什么这里多了一个typename了，
因为模板类型在实例化之前，编译器并不知道 `::boost::remove_pointer<T>::type` 具体是什么，
可能有三种可能：

- 静态数据成员
- 静态成员函数
- 嵌套类型

加上typename就是告诉编译器这里是嵌套类型。

