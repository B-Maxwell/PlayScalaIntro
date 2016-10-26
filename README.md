This project demonstrate how to create a simple CRUD application with Play.
Additionally, this project will be an example deployment to Heroku cloud PAAS (Platform As A Service).

"Download Heroku Toolbelt for.. MAC OS"
HEROKU = https://devcenter.heroku.com/categories/scala

Open terminal and cd to your project root directory.

Add the following 2 lines in a new file called Procfile in the project dir. For a project named “play-scala-intro" (defined in build.sbt).
web: target/universal/stage/bin/play-scala-intro -Dhttp.port=$PORT -Dplay.evolutions.db.default.autoApply=true -Ddb.default.driver=org.postgresql.Driver -Ddb.default.url=${DATABASE_URL}
console: target/universal/stage/bin/play-scala-intro -main scala.tools.nsc.MainGenericRunner -usejavacp

Create a Heroku account and follow the steps below. (in project dir)
Sign up for free Heroku account: https://signup.heroku.com/dc
Then in your project dir, run:
$ heroku login
$ heroku create

Copy the remote app url and git repo and save for reference later.
ie; https://rocky-everglades-71247.herokuapp.com/ | https://git.heroku.com/rocky-everglades-71247.git

Generate a Secret hash and add it to the config file:
$ sbt playGenerateSecret
and capture the string (make sure to remove any backquotes!!)
Replace (or add) the line in application.conf like this:
  play.crypto.secret = ${APP_SECRET}

Add the APP_SECRET key inside the quotes to share with Heroku:
$ heroku config:add APP_SECRET=""

Deploy to heroku remote:
$ git push heroku master

Visit the new website with either the app's url or this handy shortcut:
$ heroku open

View the log output:
$ heroku logs --tail

Once set up you can run many Heroku commands such as: heroku logs --tail heroku local etc.
