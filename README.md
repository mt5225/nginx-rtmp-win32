nginx-rtmp-win32
================

Nginx: 1.12.1  
Nginx-Rtmp-Module: 1.2.0  
openssl-1.0.2l  
pcre-8.40  
zlib-1.2.11

# configure arguments
```
nginx version: nginx/1.12.1
built by cl
built with OpenSSL 1.0.2l  25 May 2017
TLS SNI support enabled
configure arguments: --with-cc=cl --builddir=objs --prefix= --conf-path=conf/ngi
nx.conf --pid-path=logs/nginx.pid --http-log-path=logs/access.log --error-log-pa
th=logs/error.log --sbin-path=nginx.exe --http-client-body-temp-path=temp/client
_body_temp --http-proxy-temp-path=temp/proxy_temp --http-fastcgi-temp-path=temp/
fastcgi_temp --http-scgi-temp-path=temp/scgi_temp --http-uwsgi-temp-path=temp/uw
sgi_temp --with-cc-opt=-DFD_SETSIZE=1024 --with-pcre=objs/lib/pcre-8.40 --with-z
lib=objs/lib/zlib-1.2.11 --with-select_module --with-http_v2_module --with-http_
realip_module --with-http_addition_module --with-http_sub_module --with-http_dav
_module --with-http_stub_status_module --with-http_flv_module --with-http_mp4_mo
dule --with-http_gunzip_module --with-http_gzip_static_module --with-http_auth_r
equest_module --with-http_random_index_module --with-http_secure_link_module --w
ith-http_slice_module --with-mail --with-stream --with-openssl=objs/lib/openssl-
1.0.2l --with-openssl-opt=no-asm --with-http_ssl_module --with-mail_ssl_module -
-with-stream_ssl_module --add-module=../nginx-rtmp-module
```

# start server
```
.\nginx
```

# transcode using ffmpeg
```
ffmpeg -i "rtsp://192.168.86.24:8554/1080P_1.mkv" -vcodec libx264 -vprofile baseline -threads 2 -fflags +genpts -acodec aac -strict -2 -s 320x320 -f flv rtmp://127.0.0.1/live/demo.sdp
```

- `source:  rtsp://192.168.86.24:8554/1080P_1.mkv`
- `dst: rtmp://127.0.0.1/live/demo.sdp`
- `transcode:  320x320`

# view dst
```
rtmp://127.0.0.1:1935/live/demo.sdp
```

# config file
```
conf/nginx.conf
```

# status
```
http://localhost:8080/stat
```



