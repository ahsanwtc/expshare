Quick Start Guide
=================
 
 
Download ExpShare
----------------------------------------------
 
First, you need to download the ExpShare from GitHub. 
 
 
Secret Django Key
-----------------
 
The project has the **DJANGO_KEY** setting variable hidden. 
 
You can generate your DJANGO_KEY |django_key|.
 
.. |django_key| raw:: html
    
    <a href="http://www.miniwebtool.com/django-secret-key-generator"
    target="_blank">here</a>
 
 
Project Name
------------
 
This project is named *ExpShare*, so if you are using this 
project to create your own project, you'll have to change 
the name in a few places:
 
 - *expshare_project* **folder** (your top project container)
 - *expshare_project/expshare* **folder** (your project name)
 - virtual environment name: **dj183** (name it whatever you want)
 - in virtual environment **postactivate** files (see section below), you have to change **expshare.settings.development** for your **projectname.settings.development**. 

 
Virtual environment and Settings Files
---------------------------------------
 
First, you must know your Python 3 path::
 
    $ which python3
 
which is something similar to /usr/bin/python3.
 
Next, create a Development virtual environment with Python 3 installed::
 
    $ mkvirtualenv --python=/usr/local/bin/python3 dj183
 
where you might need to change it with your python path.
 
Go to the virtual enviornment folder with::
 
    $ cd $VIRTUAL_ENV/bin
 
and edit the postactivate file.:
 
    $ nano postactivate
 
You must add the lines: ::
 
    export DJANGO_SETTINGS_MODULE="expshare.settings.development"
    export SECRET_KEY="your_secret_django_key"
 
with your project name and your own secret key.
 
Next, edit the **predeactivate** file and add the line::
 
    unset SECRET_KEY
 
 
Next, install the packages in the environment::
 
    $ workon dj183
    $ pip install -r requirements/development.txt
 
 
 
Internationalization and Localization
-------------------------------------
 
Settings
********
 
The default language for this Project is **English**, and we use internatinalization to translate the text into German.
 
If you want to change the translation language, or include a new one, you just need to modify the **LANGUAGES** variable in the file *settings/base.py*. The language codes that define each language can be found |codes_link|.
 
.. |codes_link| raw:: html
 
    <a href="http://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx" target="_blank">here</a>
 
For example, if you want to use French you should include::
 
    LANGUAGES = (
        ...
        'fr', _("French"),
        ...
    )
 
You can also specify a dialect, like Luxembourg's German with::
 
    LANGUAGES = (
        ...
        'de-lu', _("Luxemburg's German"),
        ...
    )
 
Note: the name inside the translation function _("") is the language name in the default language (English).
 
More information on the |internationalization_post|. 
 
.. |internationalization_post| raw:: html
 
    <a href="http://marinamele.com/taskbuster-django-tutorial/internationalization-localization-languages-time-zones" target="_blank">TaskBuster post</a>
 
 
Translation
***********
 
Go to the terminal, inside the expshare_project folder and create the files to translate with::
 
    $ python manage.py makemessages -l de
 
change the language "de" for your selected language.
 
Next, go to the locale folder of your language::
 
    $ cd expshare/locale/ca/LC_MESSAGES
 
where expshare is your project folder. You have to edit the file *django.po* and translate the strings. You can find more information about how to translate the strings |translation_strings_post|.
 
.. |translation_strings_post| raw:: html
 
    <a href="http://marinamele.com/taskbuster-django-tutorial/internationalization-localization-languages-time-zones#inter-translation" target="_blank">here</a>
 
Once the translation is done, compile your messages with::
 
    $ python manage.py compilemessages -l de
 
 
 
Useful commands
---------------
 
A list of all the commands used to run this template::
 
    $ workon dj183
 
    $ python manage.py makemessages -l de
    $ python manage.py compilemessages -l de