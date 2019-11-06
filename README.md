1 安装nginx sudo apt install nginx
2 配置nginx在http的{}中
server {
    # 监听80端口
    listen 80;
    # 本机
    server_name localhost; 
    # 默认请求的url
    location / {
        #请求转发到gunicorn服务器
        proxy_pass http://127.0.0.1:5001; 
        #设置请求头，并将头信息传递给服务器端 
        proxy_set_header Host $host; 
    }
}
3 执行 nginx -s reload
flask部署web服务器gunicorn使用
pip install gunicorn
用法：gunicorn -w 6 -b 127.0.0.1:5001 demo.py:app
其中-w后面是开的进程个数，-b 后面是绑定的ip和端口，demo.py运行的flask程序，app是flask程序中的程序实例名
