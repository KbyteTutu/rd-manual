Wrk
=

常用参数：
- -t, --threads: 总线程数（建议为核心数的2倍即可）
- -c, --connections: http并发数（默认使用http1.1，会复用TCP链接）
- -d, --duration: 持续压测时间, 比如: 2s, 2m, 2h
- -H, --header: 添加http header, 比如. -H 'Api-key: xxx' 来添加接口认证信息
- --s, --script: 指定执行Lua脚本（可以使用Lua脚本实现更高阶的功能）
- --latency: 在控制台打印出延迟统计情况
- --timeout: http超时时间

测试Get请求，直接压测url参数即可
```bash
wrk -t 40 -c 1200 -d 10s http://myc.ink:8074/api/v1/get_test?apikey=aaa
```
测试Post请求，参数复杂时需要指定-s参数，借助lua脚本来完成数据模拟
```bash
wrk -t 40 -c 1200 -d 10s -s test.lua http://myc.ink:8074/api/v1/post_test
```
test.lua内容如下：
```lua
function ip()
    return
        math.random(1,255)..'.'
        ..math.random(1,255)..'.'
        ..math.random(1,255)..'.'
        ..math.random(1,255)
end

wrk.headers["Content-Type"] = "application/json"

function request()
    return wrk.format("POST", "/api/v1/post_test", wrk.headers, string.format('{"apikey": "miaoyc-test-apikey", "param": "%s"}', ip()))
end
```
wrk.format的说明如下：
```bash
  function wrk.format(method, path, headers, body)
    wrk.format returns a HTTP request string containing the passed parameters
    merged with values from the wrk table.
    根据参数和全局变量wrk, 生成一个HTTP rquest string
```
