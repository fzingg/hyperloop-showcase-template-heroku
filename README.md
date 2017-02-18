# Deploying HyperLoop Showcase on HEROKU (Fast way)

### INTRODUCTION

This tutorial shows how to deploy quickly the **Hyperloop showcase** on a **HEROKU** Server.

### DEPLOYING TUTORIAL

#### Setup of a new HEROKU app

```
heroku login
git clone https://github.com/heroku/ruby-getting-started.git
cd ruby-getting-started
heroku create
git push heroku master
heroku open
```
The initial HEROKU app is coming with a Rails 4.x version. We are going to upgrade it to a Rails 5.0.1 version.