##### 查询锁表
```sql
SELECT A.OWNER, --OBJECT所属用户
       A.OBJECT_NAME, --OBJECT名称（表名）
       B.XIDUSN,
       B.XIDSLOT,
       B.XIDSQN,
       B.SESSION_ID, --锁表用户的session
       B.ORACLE_USERNAME, --锁表用户的Oracle用户名
       B.OS_USER_NAME, --锁表用户的操作系统登陆用户名
       B.PROCESS,
       B.LOCKED_MODE,
       C.MACHINE, --锁表用户的计算机名称（例如：WORKGROUP\UserName）
       C.STATUS, --锁表状态
       C.SERVER,
       C.SID,
       C.SERIAL#,
       C.PROGRAM, --锁表用户所用的数据库管理工具（例如：ob9.exe）
           'alter system kill session ''' || C.sid || ',' || C.serial# ||
       ''';' "ORACKE_KILL"
  FROM ALL_OBJECTS A, V$LOCKED_OBJECT B, SYS.GV_$SESSION C
 WHERE A.OBJECT_ID = B.OBJECT_ID
   AND B.PROCESS = C.PROCESS
 ORDER BY 1, 2;
--- 查看被锁的表
  select p.spid,
       a.SERIAL#,
       c.object_name,
       b.SESSION_ID,
       b.ORACLE_USERNAME,
       b.OS_USER_NAME
    from v$process p, v$session a, v$locked_object b, all_objects c
   where p.ADDR = a.PADDR
     and a.PROCESS = b.PROCESS
     and c.object_id = b.OBJECT_ID;  
---锁表
  select p.spid,
  c.object_name,
  b.session_id,
  b.oracle_username,
  b.os_user_name
  from v$process p, v$session a, v$locked_object b, all_objects c
  where p.addr = a.paddr
  and a.process = b.process
  and c.object_id = b.object_id;
```

##### 查看那个用户哪个进程造成死锁

```sql
 select b.owner, b.object_name, i.session_id, i.locked_mode
    from v$locked_object i, dba_objects b
   where b.object_id = i.object_id
```

##### 查看连接的进程

```sql
select sid, serial#, username, osuser from v$session
```

##### 杀掉进程

```sql
 alter system kill session 'sid,serial#'
```

##### 查询数据库版本

```sql
select * from v$version;
  结果如下：
  Oracle Database 11g Enterprise Edition Release 11.2.0.4.0 - 64bit Production
  PL/SQL Release 11.2.0.4.0 - Production
  CORE    11.2.0.4.0  Production
  TNS for Linux: Version 11.2.0.4.0 - Production
  NLSRTL Version 11.2.0.4.0 - Production
```

##### 递归查询

###### prior 关键字

######   从根找所有的子节点

```sql
 select * from oa_hr_department start with deptpid = 0 connect by prior deptid = deptpid
```

######   根据儿子找到所有的前辈

```sql
  select * from oa_hr_department start with deptid = 3 connect by prior deptpid = deptid
```

##### sequence取值

```sql
  select seq.nextval from dual
  insert into(id,name) values(seq.nextval,'aaaa')
```

##### 创建表空间

```sql
CREATE  TABLESPACE "OA" DATAFILE 'C:\ORACLE\PRODUCT\10.2.0\ORADATA\ORCL\OA.DBF' SIZE 100M

  CREATE TABLESPACE "OA" 
    LOGGING 
    DATAFILE 'F:\ORACLE\ORADATA\ORCL\OA.ora' SIZE 5M EXTENT 
    MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT  AUTO 
```

##### 创建视图

```sql
create or replace view test_view as
      select *
        from tt
```

##### 小数问题

```sql
 SELECT 5/100 || '元' FROM dual
  查询结果
-------------
  .05元
  ----->节省空间0.5保存到数据库为.5
```


##### 查看表备注
```sql
SELECT * FROM USER_TAB_COMMENTS T WHERE T.TABLE_NAME IN (
       SELECT TABLE_NAME FROM ALL_TABLES WHERE OWNER='USER'
) AND T.COMMENTS IS NOT NULL;
```

##### 查看字段注释
```sql
select * from user_col_comments where table_name =''
```
##### 查看字段属性 表
```sql
SELECT * FROM USER_TAB_COLUMNS;
```

##### 更改表备注
    COMMENT ON TABLE ES_ACTIVITY_SPECIAL IS '专题活动表1';

##### 查询数据库日期
```sql
SELECT TO_CHAR(SYSDATE,'YYYY-MM-DD') FROM DUAL;
SELECT TO_CHAR(SYSDATE,'YYYY-MM-DD HH24:MI:SS') FROM DUAL ;
SELECT TO_CHAR(SYSDATE,'YYYY') FROM DUAL
```

##### 字符串处理

###### 替换字符串
```sql
replace(strSource, str1, str2) 将strSource中的str1替换成str2
解析：strSource:源字符串
　　   str1: 要替换的字符串
  　　 str2: 替换后的字符串
```

##### 希望把表1的字段B赋给表2的C字段

###### 方法1
```sql
    UPDATE  表2
    SET
      表2.C  =  (SELECT  B  FROM  表1  WHERE   表1.A = 表2.A)
    WHERE
      EXISTS ( SELECT 1 FROM   表1  WHERE   表1.A = 表2.A)   
```
###### 方法2

```sql
MERGE INTO 表2 
    USING 表1
    ON ( 表2.A = 表1.A )    -- 条件是 A 相同
    WHEN MATCHED THEN UPDATE SET 表2.C = 表1.B   -- 匹配的时候，更新
```

##### 转义特殊字符

```sql
SELECT * FROM MICROFINANCE.Mf_Borrowing_Order t WHERE t.rate like '%\%%' escape '\' ;
```

##### 根据A表跟新T表  适用于数据一对一的情况

```sql
 UPDATE T
    SET
     T.PENALTY  =  (SELECT A.PENALTY FROM B A  WHERE  A.T_ID = T.ID),
     T.FEE = (SELECT A.FEE FROM B A  WHERE A.T_ID = T.ID),
     T.DAYS =  (SELECT A.DAYS FROM B A  WHERE A.T_ID = T.ID),
     T.STATUS = '1'
    WHERE
      EXISTS ( SELECT 1 FROM A WHERE  A.T_ID = T.ID);
```

NOT IN 问题

```sql
  不生效(为何? u表存在重复? 待验证)：
    SELECT * FROM t WHERE t.mobile not in  (SELECT U.MOBILE FROM U);
  生效:
  	SELECT * FROM t WHERE t.mobile not in  (SELECT U.MOBILE FROM U WHERE u.mobile = t.mobile);
```





​      