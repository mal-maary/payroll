## Running the application

This application assumes you have a Postgres 17 running locally on your machine.

## Setting up a postgres database

The database needs to be listening on port `5432`

1. Creating a Table called `Employees`
```
CREATE TABLE Employees (
	id int,
	first_name varchar(255),
	last_name varchar(255),
	role varchar(255)
)
```
2. Create a user called `payroll_app` by running:
`CREATE USER payroll_app`

3. Grant `payroll_app` access to Employees with:
`GRANT ALL PRIVILEGES ON TABLE Employees TO payroll_app`

4. Creating a sequence with
`CREATE SEQUENCE IF NOT EXISTS employees_seq OWNED BY employees.id`

5. Grant sequence usage to user `payroll_app` with:
`GRANT USAGE, SELECT ON SEQUENCE employees_seq TO payroll_app`
