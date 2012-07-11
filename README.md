#快递查询系统#

##实现功能##

1. 查询快递（可以通过关键字查询）
    * 收件人
    * 寄件人
    * 收件地址

2. 录入快递单
    * 寄件人
        * 姓名
        * 地址
        * 联系方式
    * 收件人
        * 姓名
        * 地址
        * 联系方式
    * 快递信息
        * 快递单号
        * 快递类型
            * 文件
            * 物品
                * 重量

##实现方法##

``` c
#define NAMELEN 8
#define ADDRESS  100
typedef struct 
{
    char name[NAMELEN];
    char address[ADDRESS];
    unsigned int phone;
} people;
typedef struct
{
    unsigned int number;
    unsigned double weight;            // 重量为0即为文件
} Info;
typedef sturct                                      // 快递单结构
{
    people sender;                               // 寄件人结构
    people recipients;                        // 收件人结构
    Info info;                                            // 快递信息结构
    unsigned int count;                                        // 同一快递单计数
}express;
```

通过数组实现，定义一个元素为10的`express`结构数组，每次读取，存取均为10，存储的信息在以日期为名的文件中，文件名格式为`YearMonthDay`，文件中以逗号作为分隔符