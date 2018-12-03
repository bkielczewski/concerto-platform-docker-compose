FROM campsych/concerto-platform:master
MAINTAINER Przemyslaw Lis <przemek@concertoplatform.com>

COPY nginx/nginx.conf /etc/nginx/nginx.conf
COPY nginx/concerto.conf /etc/nginx/sites-available/concerto.conf

CMD rm -rf var/cache/* \
 && php bin/console concerto:setup \
 && rm -rf var/cache/* \
 && php bin/console cache:warmup --env=prod \
 && chown -R www-data:www-data var/cache \
 && chown -R www-data:www-data var/logs \
 && chown -R www-data:www-data var/sessions \
 && chown -R www-data:www-data src/Concerto/PanelBundle/Resources/public/files \
 && chown -R www-data:www-data src/Concerto/PanelBundle/Resources/import \
 && chown -R www-data:www-data src/Concerto/TestBundle/Resources/sessions \
 && chown -R www-data:www-data src/Concerto/TestBundle/Resources/R/fifo \
 && chown -R www-data:www-data src/Concerto/TestBundle/Resources/R/init_checkpoint \
 && rm -rf src/Concerto/TestBundle/Resources/R/init_checkpoint/* \
 && cron \
 && service nginx start \
 && php-fpm