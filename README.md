# Redirect robypomper.com

SYSTEM repository for robypomper.com redirects.

This repo contains only a simple `index.html` file that will be published as
[GitHub Pages](https://pages.github.com/). At the same time the DNS records for
the `robypomper.com` use the GitHub.io servers as `A` records.

So, when the user require the [http[s]://[www.]robypomper.com](https://www.robypomper.com)
url the DNS redirects it to the GitHub.io server where the `index.html` (or the
`404.html`) page is returned.<br/>
If the user required an `http` url, the GitHub.io server redirects it to the
`https` version of the same url.<br/>
Then, this page contains a JavaScript code that replace the `window.location`'s
protocol and domain.

That's all.


## Run

Open a browser and go to the one of the following links:
* [http://robypomper.com](http://robypomper.com)
* [https://robypomper.com](https://robypomper.com) (WARNING on certificate's name)
* [http://www.robypomper.com](http://www.robypomper.com)
* [https://www.robypomper.com](https://www.robypomper.com)

After some redirect it should display the [https://www.robypomper.org](https://www.robypomper.org)
page and url.


## Test

Execute the following `curl` command into a shell:

```shell
curl -v -L -o /dev/null http://robypomper.com 2>&1 | egrep -i "> Host:|> GET|* Connected|< Server|< Location|SSL:"

* Connected to robypomper.com (185.199.111.153) port 80 (#0)
> GET / HTTP/1.1
> Host: robypomper.com
< Server: GitHub.com
< Location: https://www.robypomper.com/

* Connected to www.robypomper.com (185.199.109.153) port 443 (#1)
> GET / HTTP/2
> Host: www.robypomper.com
< server: GitHub.com
```

