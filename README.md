# ErikaLust Front-End Challenge

Heya! Hope everything is going great.

First off, huge thanks for the opportunity, it's a nice coding challenge and I really appreciate the fact that you have given me the time.

The entire project should be pretty self-explanatory, it's a pretty straight-forward Vue app with not that much meta-programming but, if you have any doubts or questions, feel totally free of letting me know. I will be looking forward to your response and hope you see something you like :).

### Project setup

1. `git clone https://github.com/saerose/vue-frontend.git`
2. `cd ./vue-frontend && npm i`
3. `touch .env`, add variable `VUE_APP_API_KEY_V3` with value equal to your API KEY to the movie database.
4. `npm run serve`
5. app should be running in `http://localhost:8080`

### The Solution

The task was pretty straight forward and you will find the resulting app is working as expected. A couple of things I would like to highlight:
- The `.env` file is pretty useful for storing config and, since it contains sensitive information, it has been setup to be ignored by git
- I have decided to use the Sass pre-processor for convenience since it exposes certain methods and functionalities that are clearly superior to base CSS.
- Though there is some inter-dependence between components (Films, FilmList and Search), no Vuex has been used for this. The reason for this decision is double: I am of the opinion that, when it comes to small projects such as these, the least dependencies the better; and also, since there seemed to be a focus on speed of the project, this was a way of speeding up the coding. I am familiar with the redux family and have worked with it previously.
- Search bar is completely functional, you need to press `Enter` in order to search for a specific movie title. To go back to the default screen pres the `X` or delete the search terms.
