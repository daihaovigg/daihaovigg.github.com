python3.4中，MySQLDB将不再被支持，使用 sqlalchemy 时会出现no module called MySQLDB的error，在py3中将用pymysql替换。用法如下：

	import pymysql
	pymysql.install_as_MySQLdb() 
    
    
sqlalchemy与mysql使用还会出现中文无法插入的情况，将报错rollback，建立数据库时应使用`CREATE DATABASE <database> DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;`
然后，*该问题的解决方案是*：

	在sqlalchemy的创建engine连接中应写create_engine('mysql+mysqldb://root:324426@127.0.0.1:3306/weather?charset=utf8'）

重点就是后面的*'?charset=utf8'*




同时，注意python3中unicode编码为utf-8：

	u.encode('utf-8')