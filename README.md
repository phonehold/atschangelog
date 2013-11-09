# ats ChangeLog 跟进


### ATS 4.1.0 (Note)

**[ts-2323](https://issues.apache.org/jira/browse/TS-2323)**

	 添加 .include 指令
	 
	 remap.config 配置如下：
	 
	 .include /etc/trafficserver/baidu.conf
	 
	 baidu.conf 配置如下：(和正常remap中的规则一样)
	 
	 map http://www.baidu.com/	http://www.baidu.com/
	 
	 traffic_line -x 生效
	 
	 BTW: 如果只改变baidu.conf 内容，traffic_line -x 则不生效，只有改变remap.conf
	 的修改时间才会生效。最有效的办法是 touch /etc/trafficserver/remap.conf
	 然后再执行traffic_line -x
	
**[ts-2265](https://issues.apache.org/jira/browse/TS-2265)**


	删除不用的日志字段
~~prob~~

~~prcb~~

~~cgid~~

`CONFIG proxy.config.log.custom_logs_enabled INT 1` 配置customlog 的时候注意不能再引用这些字段 ()

