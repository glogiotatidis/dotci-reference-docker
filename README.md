# DotCI Reference Project using Docker images

This is a simple Python test project to serve as a reference on how to
setup [DotCI](https://github.com/groupon/DotCi) using Docker
images. There is also another
[reference project using Dockerfiles](https://github.com/glogiotatidis/dotci-reference-dockerfile).

## Notes
* `image` should point to an image with all requirements needed to run
  the tests, including `git` which is used by DotCI to clone the
  project.

* DotCi Test Execution Command Breakdown

  Within the docker image defined in `.ci.yml:image` DotCI will git
  clone and then run commands defined in `.ci.yml:command`

  Full command:

  `docker run --rm --sig-proxy=true python:3 sh -cx "git clone  --branch=master https://github.com/glogiotatidis/dotci-reference-docker /var/glogiotatidis/dotci-reference-docker && cd /var/glogiotatidis/dotci-reference-docker && git reset --hard  fdf2b5e5629c5f32a4f490d13fcb958184aec382 && python test.py"
