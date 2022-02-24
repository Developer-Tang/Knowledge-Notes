## 什么时Mybatis？

1. Mybatis 是一个半 ORM(对象关系映射) 的框架，内部通过对 JDBC 的封装实现。减少了开发过程中花费大量精力去加载驱动、创建连接、创建 statement 等繁杂的操作，只需要关注 SQL 语句本身。
2. Mybatis 可以通过 XML 或注解来配置和映射原生信息，将 Entity 映射成数据库中的记录，避免了绝大部分 JDBC 代码、手动设置参数以及手动封装结果集
3. 通过 XML 文件或注解的方式将要执行的各种 statement 配置起来，并通过 Java 对象和 statement 中的 sql 的动态参数进行映射生成最终的 sql 语句，最后由 mybatis 框架执行 sql
   并将结果映射为 java 对象返回

## Mybatis的优缺点

**优点：**

1. 基于 SQL 语句编程，SQL 语句写在 XML 中，解除了 sql 与程序代码的耦合，便于统一管理。提供 xml 标签，支持编写动态 sql，可以重用
2. 与 JDBC 相比减少了代码量，消除了 JDBC 大量的冗余代码，接替了手动处理连接创建、调用、销毁
3. 提供相关映射标签，支持对象与数据库的 ORM 字段关系映射。提供对象关系银蛇标签，支持对象关系维护
4. 与数据库具有很好的兼容性
5. 与 Spring 集成方便
6. 能很好对 SQL 进行性能优化和调整

**缺点点：**

1. SQL 语句编写工作量较大，数据量大时对开发人员的 SQL 功底有一定的要求
2. SQL 依赖于数据库，导致数据库移植性差，不能随意更换、调整数据库

## #{}与${}的区别

`#{}` 为预编译处理，Mybatis在处理 `#{}` 时会将 sql 中的 `#{}` 替换为 `?` ，调用 PreparedStatement 的 set 方法进行赋值

`${}` 为字符串拼接，Mybatis处理 `${}` 时会将 sql 中的 `${}` 直接替换成对应的值

`#{}` 能有效的防止 sql 注入，提高安全性

## 实体属性名与表中字段不一致

1. 通过在 sql 中设置别名返回与实体属性名对应的别名
2. 通过 `<resultMap>` 设置实体属性名与表字段的映射关系

## like模糊查询怎么写

1. java 代码中完成通配符添加，sql 中通过 `#{}` 注入
   ```java
   String key = "ABC"
   String likeStr = "%" + key + ""%"
   List<Table> tables =  mapper.list(likeStr);
   ```
   ```xml
   <select id="xxxx">
        select * from table where name like #{likeStr}
   </select>
   ```
2. sql 中直接拼接通配符，可能造成 sql 注入问题
   ```xml
   <select id="xxxx">
        select * from table where name like '%#{key}%'
   </select>
   ```

## mapper中如何传递多个参数？

1. 通过 `#{n}` 实现，n 为参数索引位
   ```java
   User findUser(Integer age,Integer sex);
   ```
   ```xml
   <select id="findUser">
        select * from table where age = ${0} and sex = #{1}
   </select>
   ```
2. 使用 `@Param` 注解
   ```java
   User findUser(@Param("age") Integer age,@Param("sex") Integer sex);
   ```
   ```xml
   <select id="findUser">
        select * from table where age = ${age} and sex = #{sex}
   </select>
   ```

## Mapper接口的工作原理

Mapper接口没有实现类，当调用接口时通过全限名(例：com.xxxx.user.mapper.UserMapper)+方法名拼接字符串作为 Key 值(
例：com.xxxx.user.mapper.UserMapper.findUserByName)，可唯一定位一个 MapperStatement 。在 xml 中的每一个 `<select>` 、`<insert>`
、`<update>`、`<delete>` 标签都会被解析成一个 MapperStatement 对象。Mapper 接口采用 JDK 动态代理，Mybatis 在运行时生成代理对象 proxy ，代理对象会拦截接口方法，转而执行
MapperStatement 所代表的 sql ，然后将 sql 执行结果封装放回

## Mapper接口可以重载吗？

Mapper接口中的方法不能进行重载，因为采用 **全限名 + 方法名** 的保存和寻找策略。

## Mybatis动态SQL有什么用

根据标签中表达式的值，完成逻辑判断并动态拼接sql的功能，提高了单个接口的重用性

## XML映射文件中有哪些创建的标签

**定义SQL**

- **`<insert>`**
- **`<select>`**
- **`<update>`**
- **`<delete>`**

**格式化**

- **`<where>`：** 动态添加 where 关键字，并处理条件开头通过动态 sql 可能多出来的 AND | OR
- **`<set>`：** 当动态 sql 拼接时，set 后未设置更新字段及其值时去除多余的 set 关键字
- **`<trim>`：** 与where关键字功能相似，区别在于该标签可以指定要去除的关键字

**动态SQL**

- **`<if>`：** 当 test 表达式成立时，拼接标签中的 sql
- **`<foreac>`：** 循环遍历集合元素，常用于 in 和 insert into values
- **`<choose>`：** 相当于 java 中的 switch ，当内部按顺序任意一个 `<when>` 条件成即结束，如果都不满足则使用 `<ootherwise>`
- **`<when>`：** 相当于 switch 语句中的 case ，默认带 break 的那种
- **`<ootherwise>`：** 相当于 switch 语句中的 default
- **`<bind>`：**

**结果映射**

- **`<resultMap>`：** 结果映射集
- **`<id>`：** 设置表主键字段与属性的关联
- **`<result>`：** 设置属性与字段的关联
- **`<association>`：** 设置属性与记录属于一对一关联关系，常用与属性为其他对象
- **`<collection>`：** 设置属性与记录属于一对多关联关系，常用于属性为集合

**其他**

- **`<sql>`：** 定义 SQL 片段
- **`<include>`：** 导入 sql 片段
- **`<selectKey>`：** 设置主键生成策略

## 关联查询结果封装

**一对一**

```html
<select id="findUser" resultMap="bindEntity">
    select * from student s,class c where s.c_id = c.c_id and s.s_id = #{id}
</select>
<resultMap id="bindEntity" resultType="student">
    <id property="id" column="s_id"/>
    <result property="name" column="s_name"/>
    <association property="class" javaType="class">
        <id property="id" column="c_id"/>
        <result property="name" column="c_name"/>
    </association>
</resultMap>
```

**一对多**

```html
 <select id="findUser" resultMap="bindEntity">
    select * from class c,student s where c.c_id = s.c_id and c.c_id = #{id}
</select>
<resultMap id="bindEntity" resultType="class">
    <id property="id" column="c_id"/>
    <result property="name" column="c_name"/>
    <collection property="class" javaType="class">
        <id property="id" column="c_id"/>
        <result property="name" column="c_name"/>
    </collection>
</resultMap>
```

## Mybatis的一二级缓存
