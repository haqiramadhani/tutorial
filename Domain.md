---


---

<h1 id="domain">Domain</h1>
<h2 id="add-new-domain">1. Add New Domain</h2>
<ul>
<li>edit file apache.conf</li>
</ul>
<pre><code>nano /etc/apache2/apache2.conf
</code></pre>
<ul>
<li>cari baris dengan text dibawah pastikan tidak ada tanda pagar.</li>
</ul>
<pre><code>IncludeOptional sites-enabled/*.conf
</code></pre>
<ul>
<li>buat file domain.conf</li>
</ul>
<pre><code>nano /etc/apache2/sites-available/jasadigitalin.com.conf
</code></pre>
<pre><code>&lt;VirtualHost *:80&gt;
     ServerAdmin admin@jasadigitalin.com
     DocumentRoot /var/www/html/jasadigitalin.com/
     ServerName jasadigitalin.com
     ServerAlias www.jasadigitalin.com

     &lt;Directory /var/www/html/jasadigitalin.com/&gt;
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
     &lt;/Directory&gt;

     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
RewriteEngine on
RewriteCond %{SERVER_NAME} =www.jasadigitalin.com [OR]
RewriteCond %{SERVER_NAME} =jasadigitalin.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
&lt;/VirtualHost&gt;
</code></pre>
<ul>
<li>Aktifkan domain</li>
</ul>
<pre><code>ln -s /etc/apache2/sites-available/jasadigitalin.com.conf /etc/apache2/sites-enabled/jasadigitalin.com.conf
sudo a2ensite jasadigitalin.com.conf
</code></pre>
<ul>
<li>Restart apache</li>
</ul>
<pre><code>service apache2 restart
</code></pre>
<h3 id="lets-encrypt-ssl">Let’s Encrypt SSL</h3>
<pre><code>certbot --apache
</code></pre>
<h2 id="add-database--user">2. Add Database &amp; User</h2>
<pre><code>CREATE DATABASE jasadigitalin_wp;
INSERT INTO mysql.user (User,Host,authentication_string,ssl_cipher,x509_issuer,x509_subject) VALUES('jasadigitalin_wp','localhost',PASSWORD('JasaDigitalin123'),'','','');
FLUSH PRIVILEGES;
GRANT ALL PRIVILEGES ON jasadigitalin_wp.* to jasadigitalin_wp@localhost;
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'jasadigitalin_wp'@'localhost';
</code></pre>
<h2 id="add-wordpress">3. Add Wordpress</h2>
<pre><code>cd /tmp
curl -O https://wordpress.org/latest.tar.gz
tar xzvf latest.tar.gz
mv wordpress /var/www/html/jasadigitalin.com
mkdir /var/www/html/jasadigitalin.com/wp-content/uploads
chown -R www-data:www-data /var/www/html/jasadigitalin.com
</code></pre>

