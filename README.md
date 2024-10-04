# craftinfo

Monorepo for craftinfo scripts

The general idea here that its just a lookup for scripts.
As an example. I want to add the libuv library, I need to tweak it a little for consumption in mulle-sde.
So I do:

`mulle-sde add libuv`

we can then look for `~/.mulle/share/craftinfo/libuv/add`. 
Assuming that the scripts come from the main github repository and are vetted during pull requests,
this should be safe enough.

We can then "just" execute the script, and then we have `libuv` as a ready configured dependency.
We might even add some other dependency or library that is needed.

The script then could do:

``` bash
mulle-sde dependency add --if-missing --no-craftinfo libuv
mulle-sde dependency set libuv aliases uv
mulle-sde dependency set libuv include uv.h
```

## Other ideas

* scripts should not be platform specific (like libuv.darwin), that should be done inside the script if at all
* scripts could be version specific though  (libuv/version/v1.2.3/add)
  
