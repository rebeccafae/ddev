<h1>Using the ddev command line interface (CLI)</h1>

Type `ddev` or `ddev -h`in a terminal windows to see the available ddev commands. There are commands to configure a project, start, stop, remove, describe, etc. Each command also has help. For example, `ddev describe -h`.


## Quickstart Guides

These are quickstart instructions for WordPress, Drupal 6, Drupal 7, Drupal 8, TYPO3, and Backdrop.

**Prerequisites:** Before you start, follow the [installation instructions](../index.md#installation). Make sure to [check the system requirements](../index.md#system-requirements), you will need *docker* and *docker-compose* to use ddev.

### WordPress Quickstart
To get started using ddev with a WordPress project, clone the project's repository and checkout its directory.

```
git clone https://github.com/example-user/example-wordpress-site
cd example-wordpress-site
```

From here we can start setting up ddev. Inside your project's working directory, enter the command:

```
ddev config
```

_Note: ddev config will prompt you for a project name, docroot, and project type._

After `ddev config`, you're ready to start running your project. Run ddev using:

```
ddev start
```

When `ddev start` runs, it outputs status messages to indicate the project environment is starting. When the startup is complete, ddev outputs a message like the one below with a link to access your project in a browser.

```
Successfully started example-wordpress-site
Your project can be reached at: http://example-wordpress-site.ddev.local and https://example-wordpress-site.ddev.local
```

Quickstart instructions regarding database imports can be found under [Database Imports](#database-imports).

### Drupal 6/7 Quickstart

Beginning to use ddev with a Drupal 6 or 7 project is as simple as cloning the project's repository and checking out its directory.

```
git clone https://github.com/user/my-drupal-site
cd my-drupal-site
```

Now to start working with ddev. In your project's working directory, enter the following command:

```
ddev config
```

_Note: ddev config will prompt you for a project name, docroot, and project type._

After `ddev config`, you're ready to start running your project. Run ddev using:

```
ddev start
```

When `ddev start` runs, it outputs status messages to indicate the project environment is starting. When the startup is complete, ddev outputs a message like the one below with a link to access your project in a browser.

```
Successfully started my-drupal7-site
Your project can be reached at: http://my-drupal7-site.ddev.local
```

Quickstart instructions for database imports can be found under [Database Imports](#database-imports).

### Drupal 8 Quickstart

Get started with Drupal 8 projects on ddev either by cloning a git repository or using a new or existing composer project.

**Git Clone Example**

```
git clone https://github.com/example-user/my-drupal8-site
cd my-drupal8-site
```

**Composer Setup Example**

```
mkdir my-drupal8-site
cd my-drupal8-site
ddev config --project-type php --php-version 7.1
ddev composer create drupal-composer/drupal-project:8.x-dev --stability dev --no-interaction
```

_Find more information [on composer and how to use it](https://github.com/drupal-composer/drupal-project)._

The next step is to configure ddev. In your project's working directory, enter the following command:

```
ddev config
```

_Note: ddev config will prompt you for a project name, docroot, and project type._

After `ddev config`, you're ready to start running your project. Run ddev using:

```
ddev start
```

When `ddev start` runs, it outputs status messages to indicate the project environment is starting. When the startup is complete, ddev outputs a message like the one below with a link to access your project in a browser.

```
Successfully started my-drupal8-site
Your project can be reached at: http://my-drupal8-site.ddev.local
```

### TYPO3 Quickstart

To get started using ddev with a TYPO3 project, clone the project's repository and checkout its directory.

**Git Clone Example**

```
git clone https://github.com/example-user/example-typo3-site
cd example-typo3-site
```

If necessary, run build steps that you may require, like `composer install` in the correct directory.

**Composer Setup Example**

```
mkdir my-typo3-site
cd my-typo3-site
ddev config --project-type php --php-version 7.2
ddev composer create typo3/cms-base-distribution ^9
```

_Find more information [on composer and how to use it](https://composer.typo3.org)._

From here we can start setting up ddev. In your project's working directory, enter the command:

```
ddev config
```

_Note: ddev config will prompt you for a project name, docroot, and project type._

* The project name will be part of the URL, so make sure to avoid whitespace, underscores and special characters to avoid problems down the road.
* After the command runs through, prepare to edit the generated config.yaml file:
** Review the PHP version. Available options: 5.6, 7.0, 7.1, 7.2 and 7.3.
** Review the ports the system wants to use. If you run a local stack already, you will need to adjust here, or shut down your local stack. See [additional troubleshooting information here](https://ddev.readthedocs.io/en/stable/users/troubleshooting/#unable-listen).

After you've run `ddev config`, you're ready to start running your project. To start running ddev, simply enter:

```
ddev start
```

When `ddev start` runs, it outputs status messages to indicate the project environment is starting. When the startup is complete, ddev outputs a message like the one below with a link to access your project in a browser.

```
Successfully started example-typo3-site
Your application can be reached at: http://example-typo3-site.ddev.local
```

For those wanting/needing to connect to the database within the database container directly, please see the [developer tools page](https://ddev.readthedocs.io/en/stable/users/developer-tools/#using-development-tools-on-the-host-machine).

### Backdrop Quickstart

To get started with Backdrop, clone the project repository and navigate to the project directory.

```
git clone https://github.com/example-user/example-backdrop-site
cd example-backdrop-site
```

To set up ddev for your project, enter the command:

```
ddev config
```

_Note: ddev config will prompt you for a project name, docroot, and project type._

After `ddev config`, you're ready to start running your project. Run ddev using:

```
ddev start
```

When `ddev start` runs, it outputs status messages to indicate the project environment is starting. When the startup is complete, ddev outputs a message like the one below with a link to access your project in a browser.

```
Successfully started example-backdrop-site
Your application can be reached at: http://example-backdrop-site.ddev.local
```

### Database Imports

Import a database with just one command; We offer support for several file formats, including: **.sql, sql.gz, tar, tar.gz, and zip**.

Here's an example of a database import using ddev:

```
ddev import-db --src=dumpfile.sql.gz
```

**Note for Backdrop users:** In addition to importing a Backdrop database, you will need to extract a copy of your Backdrop project's configuration into the local `active` directory. The location for this directory can vary depending on the contents of your Backdrop `settings.php` file, but the default location is `[docroot]/files/config_[random letters and numbers]/active`. Please refer to the Backdrop documentation for more information on [moving your Backdrop site](https://backdropcms.org/user-guide/moving-backdrop-site) into the `ddev` environment.

## Getting Started

Check out the git repository for the project you want to work on. `cd` into the directory, run `ddev config`, and follow the prompts.

```
$ mkdir drupal8
$ cd drupal8
$ ddev config --project-type php
$ ddev composer create drupal-composer/drupal-project:8.x-dev --stability dev --no-interaction
$ ddev config --project-type drupal8
```

Configuration files have now been created for your project. Take a look at the project's .ddev/config.yaml file.

Now that the configuration files have been created, you can start your project with `ddev start` (still from within the project working directory):

```
$ ddev start

Starting environment for drupal8...
Creating local-drupal8-db
Creating local-drupal8-web
Waiting for the environment to become ready. This may take a couple of minutes...
Successfully started drupal8
Your project can be reached at: http://drupal8.ddev.local
```

And you can now visit your working project. Enjoy!

### Configuration files
_**Note:** If you're providing the settings.php or wp-config.php and DDEV is creating the settings.ddev.php (or wp-config-local.php, AdditionalConfig.php, or similar), the main settings file must explicitly include the appropriate DDEV-generated settings file._

The `ddev config` command attempts to create a CMS-specific settings file with DDEV credentials pre-populated.

For **Drupal** and **Backdrop**, DDEV settings are written to a DDEV-managed file, settings.ddev.php. The `ddev config` command will ensure that these settings are included in your settings.php through the following steps:

* Write DDEV settings to settings.ddev.php
* If no settings.php file exists, create one that includes settings.ddev.php
* If a settings.php file already exists, ensure that it includes settings.ddev.php, modifying settings.php to write the include if necessary

For **TYPO3**, DDEV settings are written to AdditionalConfiguration.php.  If AdditionalConfiguration.php exists and is not managed by DDEV, it will not be modified.

For **Wordpress**, DDEV settings are written to a DDEV-managed file, wp-config-ddev.php. The `ddev config` command will attempt to write settings through the following steps:

* Write DDEV settings to wp-config-ddev.php
* If no wp-config.php exists, create one that include wp-config-ddev.php
* If a DDEV-managed wp-config.php exists, create one that includes wp-config.php
* If a user-managed wp-config.php exists, instruct the user on how to modify it to include DDEV settings

How do you know if DDEV manages a settings file? You will see the following comment. Remove the comment and DDEV will not attempt to overwrite it!

```
/**
 #ddev-generated: Automatically generated Drupal settings.php file.
 ddev manages this file and may delete or overwrite the file unless this comment is removed.
 */
```

## Listing project information

To see a list of your current projects you can use `ddev list`.

```
➜  ddev list
NAME     TYPE     LOCATION             URL(s)                      STATUS
drupal8  drupal8  ~/workspace/drupal8  http://drupal8.ddev.local   running
                                       https://drupal8.ddev.local
```

You can also see more detailed information about a project by running `ddev describe` from its working directory. You can also run `ddev describe [project-name]` from any location to see the detailed information for a running project.

```
NAME     TYPE     LOCATION             URL(s)                      STATUS
drupal8  drupal8  ~/workspace/drupal8  http://drupal8.ddev.local   running
                                       https://drupal8.ddev.local

Project Information
-----------------
PHP version:	7.0

MySQL Credentials
-----------------
Username:     	db
Password:     	db
Database name:	db
Host:         	db
Port:         	3306
To connect to mysql from your host machine, use port 32768 on 127.0.0.1.
For example: mysql --host=127.0.0.1 --port=32768 --user=db --password=db --database=db

Other Services
--------------
MailHog:   	http://drupal8.ddev.local:8025
phpMyAdmin:	http://drupal8.ddev.local:8036

DDEV ROUTER STATUS: healthy
```

## Importing assets for an existing project

An important aspect of local web development is the ability to have a precise recreation of the project you are working on locally, including up-to-date database contents and static assets such as uploaded images and files. ddev provides functionality to help with importing assets to your local environment with two commands.

### Importing a database

The `ddev import-db` command is provided for importing the MySQL database for a project. Running this command will provide a prompt for you to specify the location of your database import.

```
➜  ddev import-db
Provide the path to the database you wish to import.
Import path:
~/Downloads/db.sql
Importing database...
Successfully imported database for drupal8
```

<h4>Supported file types</h4>

Database import supports the following file types:

- Raw SQL Dump (.sql)
- Gzipped SQL Dump (.sql.gz)
- (Gzipped) Tarball Archive (.tar, .tar.gz, .tgz)
- Zip Archive (.zip)

If a Tarball Archive or Zip Archive is provided for the import, you will be provided an additional prompt, allowing you to specify a path within the archive to use for the import asset. The specified path should provide a Raw SQL Dump (.sql). In the following example, the database we want to import is named data.sql and resides at the top-level of the archive:

```
➜  ddev import-db
Provide the path to the database you wish to import.
Import path:
~/Downloads/site-backup.tar.gz
You provided an archive. Do you want to extract from a specific path in your archive? You may leave this blank if you wish to use the full archive contents
Archive extraction path:
data.sql
Importing database...
A settings file already exists for your application, so ddev did not generate one.
Run 'ddev describe' to find the database credentials for this application.
Successfully imported database for drupal8
```

<h4>Non-interactive usage</h4>

If you want to use import-db without answering prompts, you can use the `--src` flag to provide the path to the import asset. If you are importing an archive, and wish to specify the path within the archive to extract, you can use the `--extract-path` flag in conjunction with the `--src` flag. Example:

`ddev import-db --src=/tmp/mydb.sql.gz`

### Exporting a Database

You can export a database with `ddev export-db`, which outputs to stdout or with options to a file:

```
ddev export-db --file /tmp/db.sql.gz
ddev export-db >/tmp/db.sql.gz
ddev export-db --gzip=false >/tmp/db.sql
```

### Importing static file assets

To import static file assets for a project, such as uploaded images and documents, use the command `ddev import-files`. This command will prompt you to specify the location of your import asset, then import the assets into the project's upload directory. To define a custom upload directory, set the `upload_dir` key in your project's `config.yaml`. If no custom upload directory is defined, the a default will be used:

- For Drupal projects, this is the `sites/default/files` directory
- For WordPress projects, this is the `wp-content/uploads` directory
- For TYPO3 projects, this is the `fileadmin` directory
- For Backdrop projects, this is the `files` directory

```
➜  ddev import-files
Provide the path to the directory or archive you wish to import. Please note, if the destination directory exists, it will be replaced with the import assets specified here.
Import path:
~/Downloads/files.tar.gz
Successfully imported files for drupal8
```

<h4>Supported file types</h4>

Static asset import supports the following file types:

- A directory containing static assets
- (Gzipped) Tarball Archive (.tar, .tar.gz, .tgz)
- Zip Archive (.zip)

If a Tarball Archive or Zip Archive is provided for the import, you will be provided an additional prompt, allowing you to specify a path within the archive to use for the import asset. In the following example, the assets we want to import reside at "web/sites/default/files":

```
➜  ddev import-files
Provide the path to the directory or archive you wish to import. Please note, if the destination directory exists, it will be replaced with the import assets specified here.
Import path:
~/Downloads/site-backup.tar.gz
You provided an archive. Do you want to extract from a specific path in your archive? You may leave this blank if you wish to use the full archive contents
Archive extraction path:
web/sites/default/files
Successfully imported files for drupal8
```

<h4>Non-interactive usage</h4>
If you want to use import-files without answering prompts, you can use the `--src` flag to provide the path to the import asset. If you are importing an archive, and wish to specify the path within the archive to extract, you can use the `--extract-path` flag in conjunction with the `--src` flag. Example:

`ddev import-files --src=/tmp/files.tgz`

## Snapshotting and restoring a database

The project database is stored in a docker volume, but can be snapshotted (and later restored) with the `ddev snapshot` command. A snapshot is automatically taken when you do a `ddev remove --remove-data`. For example:

```
$ ddev snapshot
Creating database snapshot d8git_20180801132403
Created database snapshot d8git_20180801132403 in /Users/rfay/workspace/d8git/.ddev/db_snapshots/d8git_20180801132403
Created snapshot d8git_20180801132403
rfay@rfay-mbp-2017:~/workspace/d8git$ ddev restore-snapshot d8git_20180801132403
...

$ ddev restore-snapshot d8git_20180801132403
...
Restored database snapshot: /Users/rfay/workspace/d8git/.ddev/db_snapshots/d8git_20180801132403

```

Snapshots are stored in the project's .ddev/db_snapshots directory, and the directory can be renamed as necessary. For example, if you rename the above d8git_20180801132403 directory to "working_before_migration", then you can use `ddev restore-snapshot working_before_migration`.


## Interacting with your project
ddev provides several commands to facilitate interacting with your project in the development environment. These commands can be run within the working directory of your project while the project is running in ddev.

### Executing Commands in Containers
The `ddev exec` command allows you to run shell commands in the container for a ddev service. By default, commands are executed on the web service container, in the docroot path of your project. This allows you to use [the developer tools included in the web container](developer-tools.md). For example, to run the Drush CLI in the web container, you would run `ddev exec drush status`.

To run a shell command in the container for a different service, use the `--service` flag at the beginning of your exec command to specify the service the command should be run against. For example, to run the mysql client in the database, container, you would run `ddev exec --service db mysql`. To specify the directory in which a shell command will be run, use the `--dir` flag. For example, to see the contents of the `/usr/bin` directory, you would run `ddev exec --dir /usr/bin ls`.

To run privileged commands, sudo can be passed into `ddev exec`. For example, to update the container's apt package lists, use `ddev exec sudo apt-get update`.

Commands can also be executed using the shorter `ddev . <cmd>` alias.

### SSH Into Containers
The `ddev ssh` command will open an interactive bash shell session to the container for a ddev service. The web service is connected to by default. The session can be ended by typing `exit`. To connect to another service, use the `--service` flag to specify the service you want to connect to. For example, to connect to the database container, you would run `ddev ssh --service db`. To specify the destination directory, use the `--dir` flag. For example, to connect to the database container and be placed into the `/home` directory, you would run `ddev ssh --service db --dir /home`.

If you want to use your personal ssh keys within the web container, that's possible. Use `ddev auth ssh` to add the keys from your ~/.ssh directory and provide a passphrase, and then those keys will be usable from within the web container. You generally only have to `ddev auth ssh` one time per computer reboot.

### Log Access

The `ddev logs` command allows you to easily view error logs from the web container (both nginx/apache and php-fpm logs are concatenated). To follow the log (watch the lines in real time), run `ddev logs -f`. When you are done, press CTRL+C to exit from the log trail. Similarly, `ddev logs -s db` will show logs from a running or stopped db container. 

## Stopping a project

To stop the development environment for a project run `ddev stop` in its working directory. You can also stop a particular project's environment from any directory by running `ddev stop <projectname>` or stop every running project via `ddev stop --all`.

## Removing a project

To remove a project's containers run `ddev remove` in the working directory of the project. To remove any running project's containers, providing the project name as an argument, e.g. `ddev remove <projectname>`.

`ddev remove` is *not* destructive. It removes the docker containers but does not remove the database for the project. This allows you to have many configured projects with databases loaded without wasting docker containers on unused projects. `ddev remove` does not affect the project code base and files.

To remove the imported database for a project, use the flag `--remove-data`, as in `ddev remove --remove-data`. This command will destroy both the containers and the imported database contents.

## ddev Command Auto-Completion

Bash auto-completion is available for ddev. Bash auto-completion is included in the homebrew install on macOS and Linux. For other platforms, download the [latest ddev release](https://github.com/drud/ddev/releases) tarball and locate `ddev_bash_completion.sh` inside it. This can be installed wherever your bash_completions.d is. For example, `cp ddev_bash_completion.sh /etc/bash_completion.d/ddev`.

<a name="opt-in-usage-information"></a>
## Opt-In Usage Information

When you start ddev for the first time (or install a new release) you'll be asked to decide whether to opt-in to send usage and error information to the developers. You can change this at any time by editing the ~/.ddev/global_config.yaml file.

If you do choose to send the diagnostics it helps us tremendously in our effort to improve this tool. What information gets sent? Here's an example of what we might see:

![usage_stats](images/usage_stats.png)

Of course if you have any reservations about this, please just opt-out (`ddev config global --instrumentation-opt-in=false`). If you have any problems or concerns with it, we'd like to know. One person did report slow ddev command completion on a network that was apparently not friendly to sentry.io.
