# nblastwwwjb
Presently live at:

nblastwwwjb


## Test locally
```
cd /path/to/nblastwwwjb
jekyll serve
```
then navigate to http://127.0.0.1:4000/

## Deploy
After adding public key on flybrain

```sh
git remote add deploy jekyll@flybrain.mrc-lmb.cam.ac.uk:~/nblastwebsite.git

git push deploy master

git push deploy
```

## Setup on server

See http://jekyllrb.com/docs/deployment-methods/#git-post-receive-hook

and https://gist.github.com/jefferis/bc07c339606c0a65b411

but note that `jekyll build` needed the `--safe option`.

