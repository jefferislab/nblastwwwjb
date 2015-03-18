# nblastwwwjb
Presently live at:

http://flybrain.mrc-lmb.cam.ac.uk/si/nblast/www/


## Test locally

To check your edits you need to install jekyll. Some details here, but Ashley can probably advise.

https://github.com/jefferislab/jefferislabwebsite/blob/master/README.md

```
cd /path/to/nblastwwwjb
jekyll serve
```
then navigate to http://127.0.0.1:4000/

## Deploy
After adding public key on flybrain

```sh
git remote add deploy jekyll@flybrain.mrc-lmb.cam.ac.uk:~/nblastwwwjb.git

git push deploy master

git push deploy
```

## Setup on server

See http://jekyllrb.com/docs/deployment-methods/#git-post-receive-hook

and https://gist.github.com/jefferis/bc07c339606c0a65b411

but note that `jekyll build` needed the `--safe option`.

## More details

See [README-JB.md](README-JB.md) for more details.
