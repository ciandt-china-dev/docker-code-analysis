FROM ciandtchina/composer-drupal

LABEL maintainer="stevenl@ciandt.com" \
    org.label-schema.vendor="CI&T China DevOps Team" \
    org.label-schema.version="1.0"

ENV COMPOSER_HOME /usr/local/lib

# Install drupal coding standards and configure
# @see https://www.drupal.org/docs/8/modules/code-review-module/installing-coder-sniffer
RUN composer global require drupal/coder \
&& composer clear-cache \
&& ln -s /usr/local/lib/vendor/bin/phpcs /usr/local/bin/phpcs \
&& ln -s /usr/local/lib/vendor/bin/phpcbf /usr/local/bin/phpcbf \
&& phpcs --config-set installed_paths /usr/local/lib/vendor/drupal/coder/coder_sniffer/ \
&& phpcs --config-set default_standard Drupal,DrupalPractice

CMD ["phpcs"]
CMD ["phpcbf"]