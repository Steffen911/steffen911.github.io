# steffen911.github.io

This repository contains my personal blog.
It will cover interesting books, crypto, personal finance, and anything else that comes to my mind.

## Setup

This project uses [Jekyll](https://jekyllrb.com) to render.
It was set up without installing Ruby and Jekyll by utilizing Docker.

```shell
# initial setup
$ docker run --rm -it --volume="$PWD:/srv/jekyll"  --env JEKYLL_ENV=production jekyll/jekyll:3.8 jekyll new . --force
```

```shell
# serving locally
docker run --rm --volume="$PWD:/srv/jekyll" --env JEKYLL_ENV=development -p 4000:4000 jekyll/jekyll:3.8 jekyll serve
```
