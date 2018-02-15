Linux inotify for Erlang
========================

Inotify is on erlang port for the Linux inotify API allowing one to monitor
changes to files and directory in the filesystem.

* [API Documentation](https://hexdocs.pm/inotify/)
* [Rebar3 Installation (hex)](https://hex.pm/packages/inotify/)

Example
-------

    inotify_demo() ->
         inotify:start(x,y),
         TmpDir = inotify:watch("/tmp/", ?ALL),
         inotify:add_handler(TmpDir, ?MODULE, self()),

         file:open("/tmp/foo_bar_inotify_test", [read, write]),

         receive
             {[create],0,"foo_bar_inotify_test"} ->
                 io:format("Yeah!~n");
         end.


For the full example refer to the unit test:
https://github.com/sheyll/inotify/blob/master/test/inotify_test.erl


Release History
---------------

* 20180215 version 0.4.2 rebar3 and hex.pm support
* 2015???? version 0.4.1 don't build on windows
* 20130101 version 0.4.0 switch to rebar
* 20100206 version 0.3 on github
* 20090221 release 0.2 bug fix
* 20080929 initial release version 0.1
