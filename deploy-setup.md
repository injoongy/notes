# How to Deploy to Heroku

## Pre-deployment stuff
(All of this should be happening on your master branch...I think)

1. Make a `public` folder in your `server` directory.

1. In your `server.js` file, add Express middleware - add this line near the top:
  `app.use(express.static('public'));`

1. Go to `package.json` in your `app` directory and add a `copy` script: 
  `"copy": "rm -rf ../server/public && cp -R ./dist ../server/public"`

1. Add another script in your `package.json` in your App directory:
  `"build:server": "npm run build && npm run copy"`

1. Run `npm run build:server` in your `app` directory.

1. Test your app from localhost:3000.

## Heroku stuff
1. Go to Heroku and create a new app - ignore pipelines.

1. Go to Resources, search 'postgres' in the Add-Ons search and add the free version.

1. Open up a terminal window and navigate to your `server` directory (make sure you're on the master branch) and login to the Heroku CLI with `heroku login`. 
    1. (You can go back to your Heroku app page, go to the "Deploy" section, and follow the first instructions for "Deploy using Heroku Git" - ignore the "Create a new Git repository" and just make sure you login to the Heroku CLI.)

1. Go into your Heroku app page and to your Settings section, select "Reveal Config vars", and copy the value for "HEROKU_POSTGRESQL_GRAY_URL".

1. Go into your Server's .env file and comment out (by putting a '#' in front) your DATABASE_URL line and paste the value for the "HEROKU_POSTGRESQL_GRAY_URL" into there instead of your own DATABASE_URL.
    1. For example, ours was: `DATABASE_URL=postgres://mdtgbjrbjrmhzy:32773b18982f...`

1. Also add this line to your .env file as well:
  `PGSSLMODE=require`

1. In your Server directory in your terminal, run the command `heroku pg` to connect to your PGSQL database in Heroku.

1. Run your scripts as usual: `npm run db-load-all`. This should create your database in Heroku.

1. Go into your Heroku overview page and click on your "Heroku Postgres" to check your Heroku database - as long as it's saying there are tables, you're good to go. (This takes a minute or two after you run your scripts! Mash that F5 key/Cmd + R keys!)

1. Go back to your terminal (still in your `server` directory), add and commit your changes, then run `git push heroku master`.

1. It should build everything, and now you can run `heroku open` to open it in your browser!

(This is still being written...pardon the mess!)

## Notes
* If you wanna keep working without deploying to Heroku and you wanna use your local servers, just revert the changes you made in steps 5 & 6 - you can just comment out the new DATABASE_URL and PGSSLMODE lines.

* Now, pushing changes using Git still works the same as before. `git push`, etc. all still will interact with your GitHub account. If you ever want to push the changes to Heroku, you will need to execute the `git push heroku master` command. 

* An additional note to the previous bullet point: I found it slightly annoying because VS Code has built-in git tracking features for when you've made changes, but those go away as soon as you push to either Heroku or GitHub - so if you've pushed the most recent changes to Heroku, VS Code's git tracking (the color and icons next to your files in the Explorer sidebar) will disappear. BUT you still need to push these changes to your GitHub!


<!-- 1. Once done, go back to Settings and look at your config vars for your PGSQL. -->
<!-- 1. Run `npm run copy` in your App directory. (OPTIONAL)
1. Run `npm run build` in your App directory. (OPTIONAL)
1. Go to your the Settings section of your Heroku App and add your .env variables into the key-value fields -->
