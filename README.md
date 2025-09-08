<h1>Source Reference</h1>
<ul>
<li><p><strong>Maintained by</strong>:  
<a href="https://github.com/medcmu/iteru-php-apache.git" rel="nofollow noopener">MedCMU</a>
</li>
<li><p><strong>Where to get help</strong>:  
<a href="https://forums.docker.com/" rel="nofollow noopener">the Docker Community Forums</a>, <a href="https://dockr.ly/slack" rel="nofollow noopener">the Docker Community Slack</a>, or <a href="https://stackoverflow.com/search?tab=newest&amp;q=docker" rel="nofollow noopener">Stack Overflow</a>
</li>
</ul>

<h2>Installation</h2>

<h3><code>Docker Compose for 8.4.12+</code></h3>
<pre>
  <code>
    web:
      container_name: 'web'
      image: medcmu/iteru-php-apache
      restart: always
      ports:
        - "8080:80"
      environment:
        WP_REDIS_HOST: "localhost.redis"
        WP_REDIS_PORT: "6379"
        WP_REDIS_PASSWORD: "password"
      deploy:
        resources:
          limits:
            memory: 768M
      memswap_limit: 768M
      ulimits:
        nofile: {
          soft: 65536,
          hard: 65536
        }
      volumes:
        - /path/to/web:/var/www/html
        - /path/to/config/cache-headers.conf:/etc/apache2/conf-enabled/10-cache-headers.conf:ro
        - /path/to/config/mpm_prefork.conf:/etc/apache2/mods-available/mpm_prefork.conf:ro
        - /path/to/config/php.ini:/usr/local/etc/php/conf.d/00-base.ini:ro
        - /path/to/config/opcache.ini:/usr/local/etc/php/conf.d/10-opcache.ini:ro
        - /path/to/config/redis.ini:/usr/local/etc/php/conf.d/20-redis.ini
      network-mode: bridge
  </code>
</pre>
