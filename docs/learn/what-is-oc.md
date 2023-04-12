!!! warning "warning"

    This function is still in early access and might change in any time.
    Known issues:

        - Requires manual launch (and some tweaks in sushi code to make it work)
        - Calling functions with arguments isn't supported yet

**One-time-compile** tries to reduce the time of compilation (see: [how sushi works](../how-sushi-works.md)) by putting all functions from your selected library to if conditions. But, how do we pass what function to execute? This is quite simple. We use command line arguments. For example, if we want to launch a function, sushi just needs to execute this to compiled file: `f14488e5-831a-4e7a-a25f-1c94d9de4f31`.

As we saw in the example, sushi passed UUID, not function name or function path. Thats because when first running one-time-compile or re-launching it due to edits in library (see: [git tracking](../../git-tracking.md)) sushi assigns for every function one UUID. That UUID is being saved in [cache](../performance-with-cache.md), so sushi can just search for function name that we want to execute and grab the UUID without creating any name conflict.
