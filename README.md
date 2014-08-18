bearded-octo-bear
=================

A generic rails app that makes starting a new project faster.

## Init

Make a search and replace for the string "bob", if you'd like. Right now, you only need to change the db configuration and the session name located in `config/database.yml` and `config/initializers/session_store.rb` respectively.

## Database
This project uses postgres. Either change the database configuration in `config/database.yml` or create a postgres role with the same name as your linux user.

    sudo -u postgres createuser -d username

If you're using password authentication (md5) don't forget to edit the postgres configuration (usually in `/etc/postgresql/9.3/main/pg_hba.conf`, replace version accordingly) to allow it - `local all username md5`. You have to restart postgres with `sudo service postgresql restart` after editing the configuration file. To create a password authenticated user:

    sudo -u postgres createuser -d username
    sudo -u postgres psql -d postgres -c "ALTER USER username WITH PASSWORD 'password';"


## Deployment

If we have a standard deployment procedure add whatever configuration is required and describe it here. Right now we use `git pull` and the following is run by hand as needed:

  * export RAILS_ENV=production
  * bundle install
  * rake db:migrate
  * rake assets:resprite
  * rake assets:precompile
  * touch tmp/restart.txt

