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


**[ts-2245](TS-2245)**

	增加4个 cache 控制项（解决内容重复缓存 --->content duplications in cache）
	建议值为2 (安全选项，如果对自己的内容有更好的把握，可以设置为1 比如图片类的应用)

proxy.config.http.cache.ignore_accept_mismatch

Scope:	CONFIG

Type:	INT

Default:	0

Reloadable:	Yes

When with a value of 1, Traffic Server serves documents from cache with a Content-Type: header that does not match the Accept: header of the request. If set to 2, this logic only happens in the absence of a Vary header in the cached response (which is the recommended and safe use).

Note This option should only be enabled with 1 if you’re having problems with caching and you origin server doesn’t set the Vary header. Alternatively, if the origin is incorrectly setting Vary: Accept or doesn’t respond with 406 (Not Acceptable), you can also enable this configuration with a ``1`.
proxy.config.http.cache.ignore_accept_language_mismatch

Scope:	CONFIG

Type:	INT

Default:	0

Reloadable:	Yes

When enabled with a value of 1, Traffic Server serves documents from cache with a Content-Language: header that does not match the Accept-Language: header of the request. If set to 2, this logic only happens in the absence of a Vary header in the cached response (which is the recommended and safe use).

Note This option should only be enabled with 1 if you’re having problems with caching and you origin server doesn’t set the Vary header. Alternatively, if the origin is incorrectly setting Vary: Accept-Language or doesn’t respond with 406 (Not Acceptable), you can also enable this configuration with a ``1`.
proxy.config.http.cache.ignore_accept_encoding_mismatch

Scope:	CONFIG

Type:	INT

Default:	0

Reloadable:	Yes

When enabled with a value of 1, Traffic Server serves documents from cache with a Content-Encoding: header that does not match the Accept-Encoding: header of the request. If set to 2, this logic only happens in the absence of a Vary header in the cached response (which is the recommended and safe use).

Note This option should only be enabled with 1 if you’re having problems with caching and you origin server doesn’t set the Vary header. Alternatively, if the origin is incorrectly setting Vary: Accept-Encoding or doesn’t respond with 406 (Not Acceptable) you can also enable this configuration with a ``1`.
proxy.config.http.cache.ignore_accept_charset_mismatch

Scope:	CONFIG

Type:	INT

Default:	0

Reloadable:	Yes

When enabled with a value of 1, Traffic Server serves documents from cache with a Content-Type: header that does not match the Accept-Charset: header of the request. If set to 2, this logic only happens in the absence of a Vary header in the cached response (which is the recommended and safe use).

Note This option should only be enabled with 1 if you’re having problems with caching and you origin server doesn’t set the Vary header. Alternatively, if the origin is incorrectly setting Vary: Accept-Charset or doesn’t respond with 406 (Not Acceptable), you can also enable this configuration with a ``1`.





