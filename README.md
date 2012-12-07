INSTALL
-------
See install doc for complete instructions

Quick start
-----------
Create settings_dev_private.py and settings_production_private.py files
per instructions in settings_default.py file.

Symlink settings_current.py to either settings_dev.py or settings_production.py

    $ ln -s /srv/python-environments/konnen/project/settings_production.py /srv/python-environments/konnen/project/settings_current.py

Whoosh search engine needs access to custom_haystack/whoosh/*

    $ chown -R www-data:root custom_haystack/whoosh

Whoosh crontab to update index

    33 * * * * /srv/python-environments/konnen/bin/python /srv/python-environments/konnen/project/manage.py update_index --age=2 --remove # Update whoosh search index

    $ pip install -r pip-requirements.txt
    $ python project/manage.py syncdb
    $ python project/manage.py migrate

Load sms control codes

    $ manage.py loaddata sms_control

After codes loaded, configure translations via Sms_control admin section

Add in Location Post Reporter Remarks instances
    - admin url: /admin/custom/locationpostreporterremarks/
