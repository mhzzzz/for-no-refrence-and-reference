# for-no-refrence-and-reference
基于范围的for语句，无引用和有引用的用途区别
想对string对象的每个字符做点什么，最好的方法就是使用c++提供的范围for语句。
语法形式：
    for (declaration : expression)
        statement;
declararion部分负责定义一个变量，该变量被用于访问序列中的基础元素。
每次迭代，declaration部分的变量都会被初始化为expression部分的下一个元素值。
因此如果我们想统计expression中的标点个数，输出expression等操作（引用同样可以输出），就可以直接使用这种形式
例子：统计标点个数
    string s("Hello World!!!")
    decltype(s.size()) punct_cnt = 0;
    
    for (auto c : s)
        if (ispunct(c))
        ++punct_cnt;
    cout<<punct_cnt<<endl;
    
【2】使用范围for语句改变字符串中的字符
    如果想改变string对象中的字符的值，必须把循环变量定义成引用类型。
    引用只是给对象的一个别名，因此当使用引用作为循环控制变量时，这个变量实际上被依次绑定到了序列的每个元素上。
    因此，当我们调用引用时，也就间接的调用了序列的元素，也就可以通过给引用对象赋值来改变原有对象。
    
【例子】：
    把整个string对象转换为大写（只要对每个字符调用toupper()函数并将结果再赋给原字符就可以了）
    
    string s("Hello World");
    for (auto &c : s)
        c = toupper(s);
    cout<< s << endl;
