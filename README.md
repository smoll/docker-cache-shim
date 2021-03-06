# docker-cache-shim

[![CircleCI](https://circleci.com/gh/kimh/docker-cache-shim.svg?style=svg)](https://circleci.com/gh/kimh/docker-cache-shim)

Install:

```
sudo ./install.sh
```

Usage:

```
docker-cache-shim: Shell script to workaround missing docker cache feature on CircleCI

  Usage:
    docker-cache-shim pull <user>/<image>

       This will try to pull <user>/<image>:circleci-cache-$CIRCLE_BRANCH.
       When the branch is built the first time and therefore no matching cache tag
       then it will fallback to circleci-cache-master tag.

    docker-cache-shim push <user>/<image>:<tag>

       This will tag <user>/<image>:<tag> to <user>/<image>:circleci-cache-$CIRCLE_BRANCH and push to repository
       so that the cache will be picked up by docker-cache-shim pull in the next build of the branch.
       Make sure to specify <tag> so that we can automatically run "docker tag <your-image> <cache-image>".

  Options:

    -f Specify custom fallback tag instead of using circleci-cache-master.
       Only meaningful for pull and noop for push because push doesn't need fallback.

    -k Specify cache tag key. Default is $CIRCLE_BRANCH
```
