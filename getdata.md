# 查询记录

查询记录使用`GET`请求，查询结果可以是单行或者多行，可以支持id查询和条件查询，id查询的url示例如下：

```
GET /student/{studentId}:查询单个学生
```

如果不使用id查询，示例如下：



```

查询学生: GET /student

```



默认直接发这个请求会查询所有学生记录，但是可以通过参数指定过滤条件，查询参数在[api参数规范](parameter.md)中定义。



某些情况下，我们的查询并不只是在模型的记录查询，也会有业务查询，业务的查询也是使用`GET`请求，对于相同的`GET`请求，无论查询多少次，结果都应该是一致的，并且不会改变数据。比如查询班级数学成绩的平均分：



```

GET /statistics/average?classesId={classesId}&subject=math

```



这个请求是一个特定的业务api，并不是查询某个模型，一样需要使用`GET`，同时无论执行多少次，都不会导致服务端数据变化，查询的结果也不应该变化。