<h1>Source Reference</h1>
<ul>
<li><p><strong>Maintained by</strong>:  
<a href="https://hub.docker.com/u/medcmu" rel="nofollow noopener">MedCMU</a></p>
</li>
<li><p><strong>Where to get help</strong>:  
<a href="https://forums.docker.com/" rel="nofollow noopener">the Docker Community Forums</a>, <a href="https://dockr.ly/slack" rel="nofollow noopener">the Docker Community Slack</a>, or <a href="https://stackoverflow.com/search?tab=newest&amp;q=docker" rel="nofollow noopener">Stack Overflow</a></p>
</li>
</ul>

<h2>Installation</h2>

<h3><code>Docker Compose</code></h3>
<pre>
  <code>web:
      container_name: 'web'
      image: medcmu/iteru-php-apache
      restart: always
      ports:
        - "8080:80"
      volumes:
        - ./site:/var/www/html
        - ./config/apache/apache2.conf:/etc/apache2/apache2.conf
        - ./config/php/php.ini:/usr/local/etc/php/php.ini</code>
</pre>

<h3><code>Docker Run</code></h3>
<pre>
     <code>$ docker run --name some-web -v /path/to/site:/var/www/html -v /path/to/config/apache2.conf:/etc/apache2/apache2.conf -v /path/to/config/php.ini:/usr/local/etc/php/php.ini -d -p 8080:80 medcmu/iteru-php-apache</code>
</pre>

<h3><code>Version 8.0.13 extention install list</code></h3>
<pre><code>mod_rewrite, mysqli, PDO, bcmath, exif, calendar, gd, imagick, opcache, intl, zip, sodium, Redis</code></pre>

<h3><code>Version 7.4.6 extention install list</code></h3>
<pre><code>mod_rewrite, mysqli, PDO, bcmath, exif, calendar, gd, imagick, memcached, mcrypt, opcache, intl, zip</code></pre>

<h3><code>Version 7.3.9-stretch-v2 extention install list</code></h3>
<pre><code>mod_rewrite, mysqli, PDO, bcmath, exif, calendar, gd, imagick, opcache, intl, zip, Redis</code></pre>

<h3><code>Version 7.3.9-stretch extention install list</code></h3>
<pre><code>mod_rewrite, mysqli, PDO, bcmath, exif, calendar, gd, imagick, opcache, intl, zip</code></pre>

<h3><code>Version 7.3.7 extention install list</code></h3>
<pre><code>mod_rewrite, mysqli, PDO, bcmath, exif, calendar, gd, imagick, zip, opcache</code></pre>

<h3><code>Version 7.1.2 extention install list</code></h3>
<pre><code>mod_rewrite, mysqli, mcrypt, gd</code></pre>

<h3><code>EXPOSE</code></h3>
<pre><code>80/tcp</code></pre>
 
<h3><code>WORKDIR</code></h3>
 <pre><code>/var/www/html</code></pre>

<h3><code>mount volumes</code></h3>
<pre><code>/etc/apache2/apache2.conf<br/>
/usr/local/etc/php/php.ini</code></pre>

<h3><code>find your php.ini and add this</code></h3>
<pre><code>extension=zip.so<br/>
extension=imagick.so<br/>
extension=redis.so (on v.7.3.9-stretch-v2 && v.8.0.13)</code></pre>