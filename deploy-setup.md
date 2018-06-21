# How to Deploy to Heroku

## Pre-deployment stuff
(All of this should be happening on your master branch...I think)
1. Make a `public` folder in your Server directory.
1. In your `server.js` file, add Express middleware - add this line near the top:
  `app.use(express.static('public'));`
1. Go to `package.json` in your App directory and add a `copy` script: 
  `"copy": "rm -rf ../server/public && cp -R ./dist ../server/public"`
1. Add another script in your `package.json` in your App directory:
  `"build:server": "npm run build && npm run copy"`
1. Run `npm run build:server` in your App directory.
1. Test your app from localhost:3000.

## Heroku stuff
1. Go to Heroku, create new App - ignore pipelines

1. Go to Resources, search 'postgres' in the Add-Ons search and add the free version.

1. Open up a terminal window and navigate to your Server directory, and make sure you're on the master branch.

1. Go to Deploy and follow instructions for the Heroku Git deployment method - ignore the "create new git repo" section and just jump to adding the "heroku remote" section.

1. Go into your Server's .env file and either comment out (by putting a '#' in front) or delete your old DATABASE_URL line and add the Heroku-generated PG config var into there instead of your own DATABASE_URL. Ours was:
  `DATABASE_URL=postgres://mdtgbjrbjrmhzy:32773b18982f942f20e360d91c45cd670b7a91bad8a920a3acfc933ce9fea5b8@ec2-50-16-241-91.compute-1.amazonaws.com:5432/dfp87cmvt8jclb`

1. Also add this line to your .env file as well:
  `PGSSLMODE=require`

1. In your Server directory in Terminal, run the command `heroku pg` to connect to your PGSQL database in Heroku.

1. Run your scripts as usual: `npm run db-load-all`. This should create your database in Heroku.

1. Go into your Heroku overview page and click on your "Heroku Postgres" to check your Heroku database - as long as it's saying there are tables, you're good to go. (This takes a minute or two after you run your scripts! Mash that F5 key/Cmd + R keys!)

1. Go back to your terminal (still in your Server directory), add and commit your changes, then run `git push heroku master`.

1. It should build everything, and now you can run `heroku open` to open it in your browser!

(This is still being written...pardon the mess!)


<!-- 1. Once done, go back to Settings and look at your config vars for your PGSQL. -->
<!-- 1. Run `npm run copy` in your App directory. (OPTIONAL)
1. Run `npm run build` in your App directory. (OPTIONAL)
1. Go to your the Settings section of your Heroku App and add your .env variables into the key-value fields -->
