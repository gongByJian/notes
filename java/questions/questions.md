dubbo拉不到包
	确定依赖包 及 父pom是否发布

错误:
Exception in thread "main" org.apache.ibatis.exceptions.PersistenceException: 
### Error querying database.  Cause: java.sql.SQLException: Unknown system variable 'query_cache_size'
### The error may exist in xml/TestMapper.xml
### The error may involve com.zhuyizhuo.java.mybatis.mapper.UserMapper.selectByExample
### The error occurred while executing a query
### Cause: java.sql.SQLException: Unknown system variable 'query_cache_size'
	at org.apache.ibatis.exceptions.ExceptionFactory.wrapException(ExceptionFactory.java:30)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:150)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:141)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectOne(DefaultSqlSession.java:77)
	at org.apache.ibatis.binding.MapperMethod.execute(MapperMethod.java:82)
	at org.apache.ibatis.binding.MapperProxy.invoke(MapperProxy.java:59)
	at com.sun.proxy.$Proxy0.selectByExample(Unknown Source)
	at com.zhuyizhuo.java.mybatis.TestMybatis.main(TestMybatis.java:29)
Caused by: java.sql.SQLException: Unknown system variable 'query_cache_size'
	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:545)
	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:513)
	at com.mysql.cj.jdbc.exceptions.SQLExceptionsMapping.translateException(SQLExceptionsMapping.java:115)
	at com.mysql.cj.jdbc.ConnectionImpl.execSQL(ConnectionImpl.java:1983)
	at com.mysql.cj.jdbc.ConnectionImpl.execSQL(ConnectionImpl.java:1936)
	at com.mysql.cj.jdbc.StatementImpl.executeQuery(StatementImpl.java:1422)
	at com.mysql.cj.jdbc.ConnectionImpl.loadServerVariables(ConnectionImpl.java:2831)
	at com.mysql.cj.jdbc.ConnectionImpl.initializePropsFromServer(ConnectionImpl.java:2381)
	at com.mysql.cj.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:1739)
	at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:1596)
	at com.mysql.cj.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:633)
	at com.mysql.cj.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:347)
	at com.mysql.cj.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:219)
	at java.sql.DriverManager.getConnection(DriverManager.java:664)
	at java.sql.DriverManager.getConnection(DriverManager.java:208)
	at org.apache.ibatis.datasource.unpooled.UnpooledDataSource.doGetConnection(UnpooledDataSource.java:201)
	at org.apache.ibatis.datasource.unpooled.UnpooledDataSource.doGetConnection(UnpooledDataSource.java:196)
	at org.apache.ibatis.datasource.unpooled.UnpooledDataSource.getConnection(UnpooledDataSource.java:93)
	at org.apache.ibatis.datasource.pooled.PooledDataSource.popConnection(PooledDataSource.java:385)
	at org.apache.ibatis.datasource.pooled.PooledDataSource.getConnection(PooledDataSource.java:89)
	at org.apache.ibatis.transaction.jdbc.JdbcTransaction.openConnection(JdbcTransaction.java:138)
	at org.apache.ibatis.transaction.jdbc.JdbcTransaction.getConnection(JdbcTransaction.java:60)
	at org.apache.ibatis.executor.BaseExecutor.getConnection(BaseExecutor.java:336)
	at org.apache.ibatis.executor.SimpleExecutor.prepareStatement(SimpleExecutor.java:84)
	at org.apache.ibatis.executor.SimpleExecutor.doQuery(SimpleExecutor.java:62)
	at org.apache.ibatis.executor.BaseExecutor.queryFromDatabase(BaseExecutor.java:324)
	at org.apache.ibatis.executor.BaseExecutor.query(BaseExecutor.java:156)
	at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:109)
	at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:83)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:148)

原因是mysql-connector-java的版本还是6.0.6，需要升级版本到8.0.11 ，这个报错就不存在了
	<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
	<version>8.0.11</version>
	</dependency>

用mybatis在java后台insert数据，能运行但数据库没有添加成功
	是因为没有提交导致，正确代码如下：

	添加：
	        sqlSession.commit();
	        sqlSession.close();

自己给自己项目提交的代码，在github的提交记录上怎么不显示我自己的图像呢？
	本地的username和email需要和git上设置的一致