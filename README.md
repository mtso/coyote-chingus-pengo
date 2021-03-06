# coyote-chingus-pengo
A practice project to reverse engineer the Pengo bot

## Original File Structure
```yml
app/                          # Core bot backend
  |- getCommand.js            # Their WIP backend helper to search the linux man pages. (Try `/pengo bash abc` in Slack).
  |- getQuote.js              # Backend helper to return quotes. Exports 2 functions (one to get a quote by ID, one for random quote).
  |- initializeQuoteDB.js     # Run once to seed and save hard-coded quote text data into the mongoDB instance.
  `- pengo.js                 # Backend ENTRY POINT: parses Slack's /slash command text to invoke the right helper function.
images/                       # Static assets served by backend.
  |- pengo.jpg
  `- rant.png
models/                       # (The 'M' model in MVC pattern). In this case, seems like there are no Views and the Controllers are inside app/ folder).
  |- quoteSchema.js           # Holds mongoose Quote model. 
public/
  |- index.html               # Frontend landing page.
  `- pengo.jpg
Procfile                      # Specifies dyno process and run command in Heroku (during deployment).
package.json                  # npm package info.
server.js                     # ENTRY POINT: 
                              # contains app route path endpoints 
                              # ( GET /auth, GET /, POST / ) where "/" is the root
```

## Practice File Structure

```yml
README.md       # Project description.
quotes.json     # Data file to simulate database (the quote data never changes during runtime).
index.js        # node.js server entry point.
.env            # Local environment variables containing SLACK_CLIENT_ID, SLACK_CLIENT_SECRET, HOST_URL, and PORT
```

## .env

The `.env` file should contain the following variables locally. This file is not committed into Heroku. Instead, they need to be manually entered in the "Settings" tab of the Heroku application under "Config Variables".

```
SLACK_CLIENT_ID=
SLACK_CLIENT_SECRET=
HOST_URL=
PORT=
```

- `SLACK_CLIENT_ID` is the OAuth key generated by Slack.
- `SLACK_CLIENT_SECRET` is the OAuth secret that matches the key.
- `HOSTNAME` is the root of the server's URL (e.g.: https://pengo.herokuapp.com)
- `PORT` is decided by Heroku during deployment. Locally defaults to 3750 if not set.