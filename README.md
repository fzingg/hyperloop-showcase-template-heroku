# Deploying HyperLoop Showcase on HEROKU (Fast way)

### INTRODUCTION

This tutorial shows how to deploy quickly the **Hyperloop showcase** on a **HEROKU** Server.

This tutorial requires you already have the **Hyperloop showcase** running perfectly on your local environment. If it's not yet the case, please read and follow one of these 2 tutorials : [Hyperloop Showcase](https://github.com/fzingg/hyperloop-showcase) and [Hyperloop Showcase Template](https://github.com/fzingg/hyperloop-showcase-template)

### DEPLOYING TUTORIAL

#### Setup of a new HEROKU app

```
heroku login
heroku create
heroku addons:create heroku-postgresql
```

```
#config/database.yml


production:
  adapter: postgresql
  encoding: unicode
  database: hyperloop-showcase-template-heroku_production
  username: hyperloop-showcase-template-heroku
  password: <%= ENV['HYPERLOOP-SHOWCASE-TEMPLATE-HEROKU_DATABASE_PASSWORD'] %>
```

```
#Gemfile

	ruby '2.3.1'

```

```
bundle update
```

```
git add .
git commit - m "init"
git push heroku master
```
