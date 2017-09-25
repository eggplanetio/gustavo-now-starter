<h1 align="center">👨 Learn Gustavo</h1>

<h5 align="center">A quick prototype for building/learning Gustavo</h5>

---

[Gustavo](https://github.com/eggplanetio/gustavo) makes it easy to write posts in [Github Gists](https://gist.github.com/) using [markdown](https://daringfireball.net/projects/markdown/) and publish using now to a specific url.

Learn more about [Gustavo](https://github.com/eggplanetio/gustavo).

---

#### To use Gustavo 

-  You need a shell app like [terminal](https://lifehacker.com/5857046/the-best-terminal-emulator-for-mac-os-x) or [iterm](https://www.iterm2.com/version3.html). 
-  Github and Gist access, [Docker](https://www.docker.com/). 
-  It is written by mac users. Please file an [issue](https://github.com/eggplanetio/gustavo/issues) with other notes.

---

<p align="center">
  <a href="#setup">Setup</a>&nbsp;&nbsp;
   <a href="#deploy">Deploying</a>&nbsp;&nbsp;
  <a href="#further-configuration">Further Configuration</a>&nbsp;&nbsp;
  <a href="#custom-url">Custom Now Url</a>&nbsp;&nbsp;
  <a href="#cite">Cites and Thanks</a>
</p>

---

<h2 id="setup">Setup</h2>

#### create a Gustavo folder
```bash
mkdir <new gustavo repo> && cd <new gustavo repo>
```

#### create a [Github gist](https://gist.github.com/)
```md
Check out [gustavo](https://github.com/eggplanetio/gustavo)! 🚀

<meta name="title" content="This is the first Gustavo gist">
<meta name="date" content="00/00/0000"><!-- provide a date -->

```

#### create a Gustavo config
```bash
echo 'module.exports = {\n
  title: 'My gustavo blog',\n
  gistId: '<< gist id >>',\n
}' > gustavo.config.js  
```

-  To avoid [rate limiting](https://github.com/dflydev/embed-github-gist/issues/10) provide a [token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/). [Read more](#urther-configuration)

#### create a [Dockerfile](https://docs.docker.com/engine/reference/builder/)

Make sure [docker](https://www.docker.com/docker-mac) is installed

```bash

echo 'FROM eggplanet/gustavo:latest' > Dockerfile

```

#### develop [locally http://localhost:3000](http://localhost:3000)

```bash

docker build -t <gustavo blog> .

# i.e.
# ----
# docker build -t learn-gustavo .

docker run -p 3000:3000 <gustavo blog>

# i.e.
# ----
# docker run -p 3000:3000 learn-gustavo

```

---

- Here are some images for [quick reference](https://github.com/yowainwright/learn-gustavo/blob/master/documentation/image-reference.md).

---

<h2 id="deploy">Deployment</h2>

Deployment can be done with [Now](https://zeit.co/now).

### Install now
```bash
npm i now -g

```

### Login to now
```bash
now login

# provide email

# confirm login via email
```

### Supply now with deployment information
```bash
now secrets add gustavo-gist-id <ID>

# i.e.
# ----
# now secrets add gustavo-gist-id 8affba6b231ca41a0b12f1ca7b14308b

now -e GIST_ID=@gustavo-gist-id --docker

```

<h2 id="further-configuration">Further Configuration</h2>

#### provide a github access token
```javascript
module.exports = {
  title: '<< title >>',
  gistId: '<< gist id >>',
  githubToken: '<< token >>', /* github access token */
}
```

#### provide a Google Analytics Id

```javascript

module.exports = {
  title: '<< title >>',
  gistId: '<< gist id >>',
  googleAnalyticsId: 'UA-X-XXXXX' /* google analytics id */
}

```

#### Deploying via Now with a Github Access Token

```bash
# add github token 
now secrets add gustavo-github-token <TOKEN>

# add gist id 
now secrets add gustavo-gist-id=<ID>

# deploy with github token and gist id
now -e GITHUB_TOKEN=@gustavo-github-token -e GIST_ID=@gustavo-gist-id --docker

```


#### More gist writing insights

TODO 

<h2 id="custom-url">Deploying Gustavo via Now with a specific URL</h2>

Now will provide a different url everytime gustavo is deployed, to provide now with a specific url.

```bash
# provide alias

now alias now alias <gustavo blog><now special url>.sh <gustavo blog>.blog

# i.e.
# ----
# now alias now alias <gustavo blog><now special url>.sh <gustavo blog>.blog

```

<h2 id="cite">Cites and Thanks</h2>

Thanks to [Brian Gonzolaz](https://www.briangonzalez.org/) for building this awesome project and allowing me to hack on it with him. Reach out to us on the [Gustavo project](https://github.com/eggplanetio/gustavo).



