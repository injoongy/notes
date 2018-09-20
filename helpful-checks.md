Some things to check before doing literally anything else
====

You're working on a web app that uses Mongo, Express, React, and Node. You've got your components. You've got your models and your routes. But when you run `npm start`, something ain't working. Nothing's rendering to the DOM. Your dev console says some vague error in red. You're stumped.

What do you do?

Well, before you really go into a panic and dive head first into the deep end of your code, here are some basic things to check for.

## Some basic things to check for
1. **DID YOU ADD A PROXY TO YOUR WEBPACK**

   Go to your `webpack.config.js` and add these three simple lines into your `devServer` object, right under `historyApiFallback: true`.
     ```js
     proxy: {
         '/api': 'http://localhost:3000'
     }
     ```
   You can thank me later.

1. **DID YOU ADD A PROXY TO YOUR WEBPACK**

   ...did you, though?

1. **Is your server running?**

   Probably not a bad idea. Go to your server directory, and run `node server.js`. Are there any errors there?

1. **Is your MongoDB running?**

   Go to your server directory and run `gomongo`, or whatever alias you have for starting up your MongoDB instance. Then restart your server.


Hopefully this helps.