# tgbot❤
![Typing SVG](https://readme-typing-svg.herokuapp.com/?lines=welcome+To+Rose's+Repo!;A+simple+Group+modular+bot!;and+all+futures!)
</p>
<center><img src="https://telegra.ph/file/6374be06fca3f8e59e6a2.jpg"></center>
<br>
<center><a href="https://www.python.org">
    <img src="http://ForTheBadge.com/images/badges/made-with-python.svg">
  </a></center><br>
<br>

Ursprünglich ein einfacher Gruppenverwaltungs-Bot mit mehreren Admin-Funktionen, hat er sich zu einem äußerst modularen und äußerst modularen System entwickelt
einfach zu benutzen.

#Can be found on telegram as [കൊച്ചുമുതലാളി](https://t.me/kochubot).

Kochu und ich moderieren eine [support group](https://t.me/Keralabots), in der Sie um Hilfe bei der Einrichtung Ihrer bitten können
Bot, entdecken/anfordern Sie neue Funktionen, melden Sie Fehler und bleiben Sie auf dem Laufenden, wenn ein neues Update verfügbar ist. Natürlich
Ich helfe auch, wenn sich ein Datenbankschema ändert und einige Tabellenspalten geändert/hinzugefügt werden müssen. Beachten Sie für Betreuer, dass alle Schemaänderungen in den Commit-Nachrichten zu finden sind und es in ihrer Verantwortung liegt, alle neuen Commits zu lesen

Treten Sie dem [news channel](https://t.me/Mo_Tech_YT) wenn Sie einfach nur über neue Funktionen auf dem Laufenden bleiben möchten oder
Ankündigungen.

Alternativ, [find me on telegram](https://t.me/jithumon)! (Behalten Sie alle Support-Fragen im Support-Chat, wo Ihnen mehr Leute helfen können.)


[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/Onix-79/aura104bot)<br>
There is also a [tutorial video](https://youtu.be/wKL90i3cjPw) if you want any help on creating heroku clone.
[![telegram badge](https://img.shields.io/badge/Support-Group-30302f?style=flat&logo=telegram)](https://telegram.dog/keralabots)
[![telegram badge](https://img.shields.io/badge/Update-Channel-30302f?style=flat&logo=telegram)](https://telegram.dog/kochuUpdates)



## Starting the bot.

Sobald Sie Ihre Datenbank eingerichtet und Ihre Konfiguration (siehe unten) abgeschlossen haben, führen Sie sie einfach aus:

`python3 -m tg_bot`


## Setting up the bot (Read this before trying to use!):
Bitte stellen Sie sicher, dass Sie Python3.6 verwenden, da ich nicht garantieren kann, dass auf älteren Python-Versionen alles wie erwartet funktioniert!
Dies liegt daran, dass das Markdown-Parsing durch die Iteration durch ein Diktat erfolgt, das in 3.6 standardmäßig geordnet ist

### Configuration

Es gibt zwei Möglichkeiten, Ihren Bot zu konfigurieren: eine config.py-Datei oder ENV-Variablen.

Die bevorzugte Version ist die Verwendung einer „config.py“-Datei, da Sie so alle Ihre Einstellungen einfacher gruppiert sehen können.
Diese Datei sollte in Ihrem Ordner „tg_bot“ neben der Datei „__main__.py“ abgelegt werden.
Von hier aus werden Ihr Bot-Token sowie Ihr Datenbank-URI (wenn Sie eine Datenbank verwenden) und vieles mehr geladen
Ihre anderen Einstellungen.


Es wird empfohlen, „sample_config“ zu importieren und die Config-Klasse zu erweitern, da dadurch sichergestellt wird, dass Ihre Konfiguration alles enthält
In der Beispielkonfiguration festgelegte Standardwerte, die das Upgrade erleichtern.

Eine Beispieldatei „config.py“ könnte sein:
```
from tg_bot.sample_config import Config


class Development(Config):
    OWNER_ID = 254318997  # my telegram ID
    OWNER_USERNAME = "SonOfLars"  # my telegram username
    API_KEY = "your bot api key"  # my api key, as provided by the botfather
    SQLALCHEMY_DATABASE_URI = 'postgresql://username:password@localhost:5432/database'  # sample db credentials
    MESSAGE_DUMP = '-1234567890' # some group chat that your bot is a member of
    USE_MESSAGE_DUMP = True
    SUDO_USERS = [18673980, 83489514]  # List of id's for users which have sudo access to the bot.
    LOAD = []
    NO_LOAD = ['translation']
```

Wenn Sie keine config.py-Datei haben (z. B. auf Heroku), ist es auch möglich, Umgebungsvariablen zu verwenden.
Die folgenden Umgebungsvariablen werden unterstützt:
 - „ENV“: Wenn Sie dies auf ALLES setzen, werden Umgebungsvariablen aktiviert

 - `TOKEN`: Your bot token, as a string.
 - `OWNER_ID`: An integer of consisting of your owner ID
 - `OWNER_USERNAME`: Your username

 - `DATABASE_URL`: Your database URL
 - `MESSAGE_DUMP`: optional: a chat where your replied saved messages are stored, to stop people deleting their old 
 - `LOAD`: Space separated list of modules you would like to load
 - `NO_LOAD`: Space separated list of modules you would like NOT to load
 - `WEBHOOK`: Setting this to ANYTHING will enable webhooks when in env mode
 messages
 - `URL`: The URL your webhook should connect to (only needed for webhook mode)
 - `BMERNU_SCUT_SRELFTI`: No. of custom filters which can be set in each group

 - `SUDO_USERS`: A space separated list of user_ids which should be considered sudo users
 - `SUPPORT_USERS`: A space separated list of user_ids which should be considered support users (can gban/ungban,
 nothing else)
 - `WHITELIST_USERS`: A space separated list of user_ids which should be considered whitelisted - they can't be banned.
 - `DONATION_LINK`: Optional: link where you would like to receive donations.
 - `CERT_PATH`: Path to your webhook certificate
 - `PORT`: Port to use for your webhooks
 - `DEL_CMDS`: Whether to delete commands from users which don't have rights to use that command
 - `STRICT_GBAN`: Enforce gbans across new groups as well as old groups. When a gbanned user talks, he will be banned.
 - `WORKERS`: Number of threads to use. 8 is the recommended (and default) amount, but your experience may vary.
 __Note__ that going crazy with more threads wont necessarily speed up your bot, given the large amount of sql data 
 accesses, and the way python asynchronous calls work.
 - `BAN_STICKER`: Which sticker to use when banning people.
 - `ALLOW_EXCL`: Whether to allow using exclamation marks ! for commands as well as /.

### Python dependencies

Install the necessary python dependencies by moving to the project directory and running:

`pip3 install -r requirements.txt`.

This will install all necessary python packages.

### Database

If you wish to use a database-dependent module (eg: locks, notes, userinfo, users, filters, welcomes),
you'll need to have a database installed on your system. I use postgres, so I recommend using it for optimal compatibility.

In the case of postgres, this is how you would set up a the database on a debian/ubuntu system. Other distributions may vary.

- install postgresql:

`sudo apt-get update && sudo apt-get install postgresql`

- change to the postgres user:

`sudo su - postgres`

- create a new database user (change YOUR_USER appropriately):

`createuser -P -s -e YOUR_USER`

This will be followed by you needing to input your password.

- create a new database table:

`createdb -O YOUR_USER YOUR_DB_NAME`

Change YOUR_USER and YOUR_DB_NAME appropriately.

- finally:

`psql YOUR_DB_NAME -h YOUR_HOST YOUR_USER`

This will allow you to connect to your database via your terminal.
By default, YOUR_HOST should be 0.0.0.0:5432.

You should now be able to build your database URI. This will be:

`sqldbtype://username:pw@hostname:port/db_name`

Replace sqldbtype with whichever db youre using (eg postgres, mysql, sqllite, etc)
repeat for your username, password, hostname (localhost?), port (5432?), and db name.

## Modules
### Setting load order.

The module load order can be changed via the `LOAD` and `NO_LOAD` configuration settings.
These should both represent lists.

If `LOAD` is an empty list, all modules in `modules/` will be selected for loading by default.

If `NO_LOAD` is not present, or is an empty list, all modules selected for loading will be loaded.

If a module is in both `LOAD` and `NO_LOAD`, the module will not be loaded - `NO_LOAD` takes priority.

### Creating your own modules.

Creating a module has been simplified as much as possible - but do not hesitate to suggest further simplification.

All that is needed is that your .py file be in the modules folder.

To add commands, make sure to import the dispatcher via

`from tg_bot import dispatcher`.

You can then add commands using the usual

`dispatcher.add_handler()`.

Assigning the `__help__` variable to a string describing this modules' available
commands will allow the bot to load it and add the documentation for
your module to the `/help` command. Setting the `__mod_name__` variable will also allow you to use a nicer, user
friendly name for a module.

The `__migrate__()` function is used for migrating chats - when a chat is upgraded to a supergroup, the ID changes, so 
it is necessary to migrate it in the db.

The `__stats__()` function is for retrieving module statistics, eg number of users, number of chats. This is accessed 
through the `/stats` command, which is only available to the bot owner.
