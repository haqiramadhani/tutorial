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

