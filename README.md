This project demonstrate how to create a simple CRUD application with Play.
Additionally, we use this project to show how to deploy to Heroku...

HEROKU = https://devcenter.heroku.com/categories/scala

Create a Heroku account and follow the steps below. (in project dir)
$ heroku login
$ heroku create

Copy the remote app url and git repo and save for reference later.
ie; https://rocky-everglades-71247.herokuapp.com/ | https://git.heroku.com/rocky-everglades-71247.git

Deploy to heroku remote:
$ git push heroku master

Visit the new website with either the app's url or this handy shortcut:
$ heroku open

View the log output:
$ heroku logs --tail

Add the following 2 lines in a new file called Procfile in the project dir. For a project named “play-scala-intro" (defined in build.sbt) this is the command to run it on some port. And note this app is deployable to Stage (sbt stage).
web: target/universal/stage/bin/play-scala-intro -Dhttp.port=${PORT}
console: target/universal/stage/bin/play-scala-intro -main scala.tools.nsc.MainGenericRunner -usejavacp
“Download Heroku Toolbelt for.. MAC OS”
git push …
etc. Once set up you can run many Heroku commands such as: heroku logs --tail heroku local etc.
