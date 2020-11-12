### MySQL和Oracle数据库中SQL语句

> 以表items为例，字段为`id,name,price,num,pic,createtime,detail,city`
>
> 实体类属性字段与数据库字段相同。

```java
private Integer id; 
private String name; 
private Float price; 
private int num; 
private String pic; 
private Date createtime;
private String detail;
private String city;

get....  //省略get方法
set....  //省略set方法
```



#### 1. 在模糊查询中的区别

##### mysql

```sql
and name like concat('%',#{name,jdbcType=VARCHAR},'%')
```

##### oracle

```sql
and name like '%'||#{name,jdbcType=VARCHAR}||'%'
```

#### 2. 在分页时的区别

##### mysql

```sql
select * from items limit 0,10     #第一页，每页10条
select * from items limit 10,10     #第二页，每页10条
select * from items limit [开始条数，int],[每页条数，int]


select count(*) from items  #查询出总条数，用于计算总页数
```

##### oracle

orcale的分页比较复杂

```sql
select count(*) from db_project #查询出总条数，用于计算总页数
 
 #oracle分页，startRow为开始条数，endRow为结束条数
 #  &gt; 是 ’>‘ 在mybatis中的转义字符
 #  &lt; 是 ‘<‘ 在mybatis中的转义字符
select id,name,price,num,pic,createtime,detail,city from
   (select id,name,price,num,pic,createtime,detail,city,ROWNUM AS rowno from
       (
           select id,name,price,num,pic,createtime,detail,city
           from db_project
        )
   )
   <where>
       <if test="startRow != null and endRow != null">
           and rowno &gt; #{startRow,jdbcType=INTEGER} and rowno &lt;= #{endRow,jdbcType=INTEGER}
       </if>
   </where>  
```

