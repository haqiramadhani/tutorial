---


---

<h1 id="installing-docker">Installing Docker</h1>
<p>Update list of package:</p>
<pre><code>sudo apt update
</code></pre>
<p>Install prerequisite package:</p>
<pre><code>sudo apt install apt-transport-https ca-certificates curl software-properties-common
</code></pre>
<p>Add repository:</p>
<pre><code>curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
</code></pre>
<p>Add docker to apt:</p>
<pre><code>sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
</code></pre>
<p>Update list of package:</p>
<pre><code>sudo apt update
</code></pre>
<p>Make sure:</p>
<pre><code>apt-cache policy docker-ce
</code></pre>
<p>Install docker:</p>
<pre><code>sudo apt install docker-ce
</code></pre>
<p>Check status:</p>
<pre><code>sudo systemctl status docker
</code></pre>
<h1 id="execute-docker-without-sudo">Execute docker without sudo</h1>
<pre><code>sudo usermod -aG docker ${USER}
su - ${USER}
id -nG
sudo usermod -aG docker [USERNAME]
</code></pre>
<h1 id="manage-docker">Manage Docker</h1>
<p>menghapus image</p>
<pre><code>docker image rm haqiramadhani/wamt
</code></pre>
<p>membuat image</p>
<pre><code>docker build -t haqiramadhani/wamt .
</code></pre>
<p>publish docker image to registry</p>
<pre><code>docker push haqiramadhani/wamt:latest
</code></pre>
<p>download image from registry</p>
<pre><code>docker pull haqiramadhani/wamt:latest
</code></pre>
<p>create container from image</p>
<pre><code>docker container create --name wamt6285311160970 -p 80:8080 -e PORT=8080 haqiramadhani/wamt:latest
</code></pre>
<p>start container</p>
<pre><code>docker container start wamt6285311160970
</code></pre>
<p>check memory usage of container</p>
<pre><code>docker ps -q | xargs docker stats --no-stream
</code></pre>

