# Build a full stack web application using React, NodeJS, PostgreSQL And Docker.

Hello world! 

One of my year propouses is to help new devs to start in the industry, since I feel very grateful with this industry which has gave a lot of great things, I want to help other folks to reach their goals.

In this tutorial I will show you an approach to build a full stack web application using React, NodeJS, PostgreSQL and Docker. The idea is to show you how you can use this tools to build your own projects.

# What we are going to build?
Since we are using a number of different tools I thought it was a good idea to keep the project simple because this is not a tutorial about react or about express or about postgres, my intention is to give you a picture of what you can achieve by combining this tools, so we are not going to go deep with each of them, and I am assuming you have some knowledge about this topics, anyway feel free to get in touch if you have any doubts about the stuff we are going to see ahead. 

So for this tutorial we are going to build a small inventory system for stores. 

The application will have only one view containing a table with the list of the products we have in our inventory and will allows us to create, edit and delete products as needed.

And at the end should looks something like this:

[TODO: INSERT IMAGE HERE]()

So said that lets get into it and happy hacking folks!

# What the heck is a full stack web applicartion?
Ok I like to make this tutorials for those who are striving in their path to become a web developer, so if you already are a fullstack dev maybe you will find this not that useful, but if you are starting I think this could be a useful way to understand how to start.

A full stack web application means that we are going to build a client and a server which will allows us to interact with a postgresql database through `http` endpoints, with this knowledge you will be able to build your own web projects.

Let's get started with the project structure.

# Project structure
In your  development workspace create a new directory called `fullstack-webapp` (your development workspace should be a directory where you put all your dev stuff, In my case I have a directory called `dev` where I put all the sh*t I build), inside your new directory create two directories: `client` and `server`, and thats it.

# The database
From their official website:
```
PostgreSQL is a powerful, open source object-relational database system with over 30 years of active development that has earned it a strong reputation for reliability, feature robustness, and performance.
```

If you want go deep into postgres you should take a look into their official [website](https://www.postgresql.org/)

PostgreSQL is a great tool used widely in the industry, even in my day job we use posgtgres as our database... actually in my three previous job was our main database.

For our project we are going to use docker to avoid the need of installing postgres on your system. If you are not familiar with docker I will leave you some useful links on how to install docker in mac and linux, also I have to tell you that a dockerized database is just for development propouses, for your production environment I would recommend using a cloud service like [AWS](https://aws.amazon.com/es/rds/postgresql/) or [Google Cloud](https://cloud.google.com/sql/?&utm_source=google&utm_medium=cpc&utm_campaign=latam-MX-all-es-dr-bkws-all-all-trial-b-dr-1007178-LUAC0009348&utm_content=text-ad-none-none-DEV_c-CRE_357184932399-ADGP_BKWS+%7C+Multi+~+Developers+%7C+PostgreSQL-KWID_43700043804513008-kwd-659080584880-userloc_9047093&utm_term=KW_%2Bgoogle%20%2Bpostgresql-ST_%2BGoogle+%2BPostgreSQL&gclid=CjwKCAiApOvwBRBUEiwAcZGdGKuKu0zJ2PEU8tD8l_OGWMLVhhkO9wntNcUgV1qdxGNKfGgnyb4g0RoCXBoQAvD_BwE&gclsrc=aw.ds) which offers managed postgres databases, also platforms such as heroku have services but are limited to be used just along with heroku.

To install docker on mac I have found this awesome post which uses brew to install all the necessary tools: https://pilsniak.com/how-to-install-docker-on-mac-os-using-brew/

Anyway I suggest to follow the official docs for each system: https://docs.docker.com/

Once you have installed docker and docker compose I have prepared a docker-compose file for your database service here: https://github.com/LuisAcerv/dockerized-postgresql-database (You can follow me at github for more nerdy stuff).

In your server directory create a new file called `docker-compose.yml` and a dotenv file `.env`

The docker-compose.yml file looks something like this:
```yaml
version: "3"
services:
  #  Create a service named db.
  db:
    #   Use the Docker Image postgres. This will pull the newest release.
    image: "postgres:10"
    #   Give the container the name postgresql_dev. You can changes to something else.
    container_name: "postgresql_dev"
    #   Setup the username, password, and database name. You can changes these values.
    environment:
      - POSTGRES_USER
      - POSTGRES_PASSWORD
      - POSTGRES_DB
    #   Maps port 5432 (localhost) to port 5432 on the container. You can change the ports to fix your needs.
    ports:
      - "5432:5432"
    #   Set a volume database so data is not lost after shutting down the container.
    #   I used the name postgres-data but you can changed it to something else.
    volumes:
      - ./postgres-data:/var/lib/postgresql/data
```

And your `.env` file:
```bash
POSTGRES_USER=docker
POSTGRES_PASSWORD=docker
POSTGRES_DB=app_dev
```

To start your postgres service just run the following command:
`docker-compose up -d` 

Then run `docker ps` to see your fresh and shinny postgres container, and thats it, now we have a databse  which we can access at `http://localhost:5432`.

## Creating the db schema
Now we have a postgres database in docker we need to create the schema for our application.

# The API

# The client

# Profit
