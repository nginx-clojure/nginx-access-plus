Nginx-Access-Plus
=============

Nginx-Access-Plus is a [Nginx](http://nginx.org/) module allows limiting access to certain http request methods and client addresses.


Installation
=================

```shell
#If nginx source is checked out from hg, please replace ./configure with auto/configure
$./configure \
    --add-module=nginx-access-plus/src/c
$ make
$ make install
```


User Guide
=================

Only Allow GET and HEAD Method
-----------------

```nginx
location / {
    allow_method all get|head;
    deny_method  all all;
}
```

All GET and HEAD Method But Deny All POST|DELETE Requests Except for 192.168.1.*
-----------------

```nginx
location / {
    allow_method all get|head;
    allow_method 192.168.1.0/24 post|delete;
    deny_method  all all;
}
```

Deny POST|PUT|DELETE Requests from 192.168.1.*
-----------------

```nginx
location / {
    deny_method  192.168.1.0/24 post|put|delete;
}
```

License
=================
Copyright © 2015 Zhang, Yuexiang (xfeep) and released under the BSD 3-Clause license.

