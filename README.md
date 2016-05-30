## react-starter-app

Build a React.js app with a compile, bundle, and test pipeline already in place.

### Development

Get [Docker](https://docs.docker.com/linux/step_one/) (preferably [Docker Mac Beta](beta.docker.com) if you're on a Mac). Fork this repository.

#### In Docker

Start the containers, and write your application.

```
$ docker-compose up -d
$ docker-compose logs -f
```

[Docker Mac](https://blog.docker.com/2016/03/docker-for-mac-windows-beta/) is supported. To activate it

```
$ echo "DOCKER_MAC_BETA=1" >> .env
```

Visit `http://$(docker-machine ip):8080` to see your changes if you're not using Docker Mac, else visit `http://localhost:8080`.

#### Debugging

Development tooling includes

- sourcemaps
- [Redux DevTools](https://github.com/gaearon/redux-devtools#chrome-extension) - for monitoring state and "time travel"
- [React DevTools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) - inspect components in the DOM

### Organization

[By feature; with tests alongside source](http://marmelab.com/blog/2015/12/17/react-directory-structure.html) - though there aren't tests yet.

### Production

Set `NODE_ENV=production` in `.env`, then

```
$ docker-compose up -d
```

The build directory in the container is `/var/www/react-docker-app/dist`. These files are served by an [NGINX](https://www.nginx.com/) front-end. Logs are located in `/var/www/react-docker-app/logs`. 

#### ES6 and SASS modules

ES6 and SASS modules can be imported using relative file URLs or using Webpack's module resolution from the root `app/`

```javascript
import { ... } from 'auth' // maps to './auth';
import { ... } from 'util' // maps to './util';
```

```sass
@import '~app.scss';
@import '~counter/counter.scss';
```

### Features

- [x] React.js v15.0.x
- [x] React Router
- [x] Redux
- [x] Redux Thunk
- [x] ES6 everywhere
- [x] JSX/SASS Hot Reloading
- [x] [Material UI](https://github.com/callemall/material-ui)
- [x] sourcemaps
- [x] continuous bundling
- [x] continuous linting
- [ ] continuous testing
- [ ] minification when `NODE_ENV=production`


