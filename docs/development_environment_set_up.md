### Installation issues

## PostgreSQL
Install the pg gem. You’ll need to include the following options to set your path and DDainclude the needed headers:

```bash
gem install pg -- --with-pg-config=/Applications/Postgres93.app/Contents/MacOS/bin/pg_config --with-pg-include='/Applications/Postgres93.app/Contents/MacOS/include/'
```
**Note that you may need to adjust these lines depending on the exact name of your Postgres.app application. Example:
If your application is named Postgres93, then “Postgres.app” will need to be changed to “Postgres93.app” in both places.

### Install using brew

`brew install postgres`

`psql -V` - to get the version of postgres

`which psql` - to figure out where postgres was installed: returns eg `/Applications/Postgres93.app/Contents/MacOS/bin/psql`

`bundle config build.pg --with-pg-config=/Applications/Postgres93.app/Contents/MacOS/bin/pg_config`

install: http://postgresapp.com/

We recommend installing: http://postgresapp.com/

First error is usually `"role 'postgres' does not exist (PG::ConnectionBad)"`

Resolve this by running `CREATE USER postgres CREATEDB;` from the psql prompt (click the elephant icon and select "open psql" OR `createuser -s -r postgres` from command line if you have psql in your path

Another error occurs on OSX without `"host: localhost"` in the database.yml could not connect to server: No such file or directory Is the server running locally and accepting connections on Unix domain socket `"/var/pgsql_socket/.s.PGSQL.5432"`?

if psql doesn't run from the command line try: add `export PATH="/usr/local/bin:$PATH"` to your `.bash_profile `to make sure you are talking to the postgres.app that's installed rather than the non-running postgresql that comes with OSX

OSX no longer needs host: `localhost` in `database.yml` if you export PG_HOST=localhost in .bash_profile

* Ubuntu
* Mac
* Capybara-webkit
* Heroku deployment


## capybara-webkit gem

The `capybara-webkit` gem needs the Qt toolchain (including qmake and the webkit library and header files). You want version 4.8 or later. To install them in Ubuntu release 12.04 LTS "precise pangolin", or later, run:

     sudo apt-get install libqtwebkit-dev

This command also works on Debian 7.

If you have an older version of Ubuntu, you can install a new version from scratch, or upgrade with `sudo do-release-upgrade`. If on Amazon EC2, see http://gregrickaby.com/safely-update-an-ubuntu-ec2-instance-on-amazon-aws/

For other platforms, see http://qt-project.org/downloads.

Note that on Mac, even after performing the aforementioned install, you are likely to need to install something else to get the `qmake` build tool. Install [Homebrew](http://brew.sh/), if you don't have it already, then run `brew install qt`. Then you should be able to run `gem install capybara-webkit -v '1.0.0'` successfully.

After that try running `bundle install` again.

## Phantomjs

On Linux run `sudo apt-get install phantomjs`

On older versions of ubuntu (like the one that the saasbook vm is created upon) this installs an old version of phantomjs.
You will need version 1.8.1.  Please see this [gist](https://gist.github.com/jezgomez/5019242) for instructions.

If you have already installed the old phantomjs run `sudo apt-get remove phantomjs` to remove it first.

## Updating Rails
Run `bundle update rails`
You might get an error with `libv8`

On OSX:

```shell
gem uninstall libv8
brew install v8
gem install therubyracer
gem install libv8 -v '3.16.14.3' -- --with-system-v8
```

[Note: this document used to be at https://github.com/AgileVentures/WebsiteOne/wiki/Development-environment-set-up]
