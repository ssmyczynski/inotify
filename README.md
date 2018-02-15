Linux inotify for Erlang
========================

Inotify is on erlang port for the Linux inotify API allowing one to monitor
changes to files and directory in the filesystem.

* [AIP-Documentation]()
* [Installation]()

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


License
-------
In short, you can do anything you want with the code including using it as part
of you plan for world domination (if your successful can I have one of the nicer
countries please). No responsiblity it taken for the fitness of the any purpose,
etc, etc. The only thing I ask is that if you find a bug and fix send me the
patch. Likewise, feature suggestions and patches are welcome.


Release History
---------------
20180215 version 0.4.1 Rebar3 Support
20130101 version 0.4.0 switch to rebar
20100206 version 0.3 on github
20090221 release 0.2 bug fix
20080929 initial release version 0.1
