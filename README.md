# Rider Templates for UE5

Source: https://github.com/XistGG/Rider-Templates-UE5

When Rider first starts up, it reads `Engine/Content/Editor/Templates/*.template` to initialize the
template files to use for UE5.

For changes to the templates to take effect, you need to clear out Rider's cache.  You can either just
remove the `.idea` directory and relaunch Rider, or you can see
[this forum post](https://rider-support.jetbrains.com/hc/en-us/community/posts/360010619699-Rider-for-Unreal-Engine-custom-file-templates)
for more details on how to do it without losing all other settings.

# Using this repo

To use this repo, after checking out the engine, and after downloading all of its content, replace the
`Engine/Content/Editor/Templates` directory with this repository.

As you change branches on the editor and re-download content for other branches, it may be necessary
to overwrite the changes with this repository multiple times.

Note however that Rider only looks ONCE for these files, then caches their values, so it should not technically
be required to constantly update this.
