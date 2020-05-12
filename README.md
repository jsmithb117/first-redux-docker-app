This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app), using the [Redux](https://redux.js.org/) and [Redux Toolkit](https://redux-toolkit.js.org/) template.

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify


Build Log:

Did:
  npx create-react-app first-redux-docker-app --template redux
  git init

created new repo on github
Did:
  git remote add origin https://github.com/jsmithb117/first-redux-docker-app.git
  git push -u origin master

Following tutorial on how to dockerize the project from:
  https://mherman.org/blog/dockerizing-a-react-app/
  It's not very explicit.  It says 'Add a Dockerfile to the project root:'
    What the fuck is a Dockerfile? is it just a file with the name Dockerfile with no extension?
      "Here's how to make a Dockerfile: 'Make a Dockerfile'.  No fucking shit?!  Terrible...  If I already knew what a Dockerfile was, I wouldn't be following this tutorial.  It should say: 'Make a file named Dockerfile with no extension in the project root'.
  Anyway, moving along...
  Made a file named 'Dockerfile' with no extension in the root project directory and populated it with the data on the tutorial.
  Made a file named '.dockerignore' in the root project directory and populated it with the data on the tutorial.
  Tried to follow instructions and ran 'docker build -t sample:dev .'
    Got error: Command 'docker' not found, but can be installed with:sudo apt install docker.io
    This tutorial is fucking terrible.  I don't want this shit installed globally unless necessary.  Trying npm install with a --save-dev
    Did:
      npm install docker --save-dev
    Once more, stupid fucking errors.  I don't want docker installed globally but I guess I don't have a choice.  It did say "Install Create React App globally:" at the beginning, so they do understand that you need software to be installed before doing this project, but apparently are so short sighted that they assume you've already installed Docker and know how to use it.  Once again, if I knew how to use it, I wouldn't be using this (terrible) tutorial.  Guess I'm installing it globally.
    Did:
      npm install -g docker
        docker installed a bunch of deprecated software as dependencies.  I am NOT getting a warm and fuzzy about Docker.
      docker build -t sample:dev .
        It actually worked this time.
      Also installed the Docker extension for VSCode.  Who knows what that's going to do...
      Did:
        docker run \
          -it \
          --rm \
          -v ${PWD}:/app \
          -v /app/node_modules \
          -p 3001:3000 \
          -e CHOKIDAR_USEPOLLING=true \
          sample:dev
      I have no idea what that did, but it didn't return any errors.
        The docs show exactly what each line does but many of them have a 'you might get an error. We didn't feel like writing the docs so read this book on stackOverflow to find out why.
          I went to the SO article and it's WAY over my head at this point.  I know almost nothing about Docker, which is why I'm using this shitty tutorial.
  Following instructions, I went to http://localhost:3001/  in browser.  Response: This site can’t be reached
    Why am I not surprised that this is not working?  It's because Docker seems to have garbage instructions, that's why.

  Last entry:
    Fuck Docker.  Maybe after I learn how to use Docker, I can come back and do this tutorial on how to use Docker...  Rating 0/7.
