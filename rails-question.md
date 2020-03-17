## Rails Questions

### Difference between rake db:migrate db:reset and db:schema:load

- **db:migrate** runs (single) migrations that have not run yet.
- **db:create** creates the database
- **db:drop** deletes the database
- **db:schema:load** creates tables and columns within the (existing) database following schema.rb

- **db:setup** does db:create, db:schema:load, db:seed
- **db:reset** does db:drop, db:setup
- **db:migrate:reset** does db:drop, db:create, db:migrate

Typically, you would use db:migrate after having made changes to the schema via new migration files (this makes sense only if there is already data in the database). db:schema:load is used when you setup a new instance of your app.

I hope that helps.

---

UPDATE for rails 3.2.12:

I just checked the source and the dependencies are like this now:

- **db:create** creates the database for the current env
- **db:create:all** creates the databases for all envs
- **db:drop** drops the database for the current env
- **db:drop:all** drops the databases for all envs
- **db:migrate** runs migrations for the current env that have not run yet
- **db:migrate:up** runs one specific migration
- **db:migrate:down** rolls back one specific migration
- **db:migrate:status** shows current migration status
- **db:rollback** rolls back the last migration
- **db:forward** advances the current schema version to the next one
- **db:seed** (only) runs the db/seed.rb file
- **db:schema:load** loads the schema into the current env's database
- **db:schema:dump** dumps the current env's schema (and seems to create the db as well)

* **db:setup** runs db:schema:load, db:seed
* **db:reset** runs db:drop db:setup
* **db:migrate:redo** runs (db:migrate:down db:migrate:up) or (db:rollback db:migrate) depending on the specified migration
* **db:migrate:reset** runs db:drop db:create db:migrate

For further information please have a look at https://github.com/rails/rails/blob/v3.2.12/activerecord/lib/active_record/railties/databases.rake (for Rails 3.2.x) and https://github.com/rails/rails/blob/v4.0.5/activerecord/lib/active_record/railties/databases.rake (for Rails 4.0.x)
