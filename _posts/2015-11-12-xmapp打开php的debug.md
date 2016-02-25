安装xampp后，打开php.ini文件，取消最后面的[XDebug]的注释，特别注意 一定要打开元调试功能：xdebug.remote_enable = 1，重启xampp的apache服务。

	[XDebug]
	zend_extension = "\xampp\php\ext\php_xdebug.dll"
	xdebug.profiler_append = 0
	xdebug.profiler_enable = 1
	xdebug.profiler_enable_trigger = 0
	xdebug.profiler_output_dir = "\xampp\tmp"
	xdebug.profiler_output_name = "cachegrind.out.%t-%s"
	xdebug.remote_enable = 1
	xdebug.remote_handler = "dbgp"
	xdebug.remote_host = "127.0.0.1"
	xdebug.trace_output_dir = "\xampp\tmp"
    
注意xdebug.remote_enable=1 。