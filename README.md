m8ball
======

Lifted from [LYSE](http://learnyousomeerlang.com/distributed-otp-applications)

Config
------

config files in $ROOT/config directory have hostnames of erlang vms hardcoded
. Need to find out how to supply hostnames as env vars
 
 
Environment
-----------
 
Ran with Erlang 17. no other requirments

Build
------

rebar clean co

No dependencies

Test
----
rebar ct (only works if config set up)


Run application
---------------

Start cluster nodes in separate terminals using

```
erl -sname a -config config/a -pa ebin/
erl -sname b -config config/b -pa ebin/
erl -sname c -config config/c -pa ebin/
```
In each erlang terminal start m8ball and crypto applications

```erlang
[ application:start(AppName) || AppName<- [crypto, m8ball]].
```


Start asking questions
```
(a@MBR13-rgibson)2> m8ball:ask("If I crash, will I have a second life?").
<<"Yes">>
(a@MBR13-rgibson)3> m8ball:ask("If I crash, will I have a second life?").
<<"Yes">>
(a@MBR13-rgibson)4>  m8ball:ask("If I crash, will I have a second life, please?").
<<"Doubtful">>
(a@MBR13-rgibson)5>
```

More usage on [LYSE](http://learnyousomeerlang.com/distributed-otp-applications)
