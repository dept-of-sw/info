What is needed to work on the project?

IDEs
- vscode
- other

VCS (version control)
- git

Virtual Machines
- Docker
- K8
- anything else

Any browser to target
- Chrome/Chromium based
- Firefox
- not Edge (Chromium based)
    - this is css specific, some things are weird, and eventually should be resolved.

----

What will the project dependencies consist of?

First, I would add that we should sit down and discuss what would be used. Conventional services would be identified and settled.

For now, I'll just put down the following. It shouldn't matter what is used in the end, as long as the project behaves the same.

Frontend: ReactJS/Vite/sass
Reasoning
- hot reload
- vite creates a lean payload for the browser for a quick page response time.
- react is pretty straightforward when it comes to frontned development.
- sass is compatible with the USWDS library target.
    - (vanilla css is not hard to use either, any other framework is really only helpful if you're going to build a 50 page site with vanilla html)

Backend: .NET 7+ minimal api + swagger, PostgreSQL, Redis
- .NET 7 is a feature-rich programming language that has a great foundation and ecosystem. It's also backed by a trillion dollar company which throws money at its continued development.
- swagger is an api spec framework. This allows us to depict the api and the contracts between our backend and the frontend. Useful in a documentation sort of way as well.
- PostgreSQL is a database which is well established and maintained.
- Redis is a service which gives us the caching and memory utility for data in transit, so we can take advantage of caching, messaging queues, etc etc.

### Note
Not everything will be used to its fullest capacity. For example, having a queue with redis may not be useful for a service which is really just a quiz system. However, we can leverage the caching system to avoid bombarding the service that processes the same payloads repeatedly. If we cache those responses to multiple of the same request, we can serve the content which the service would have produced anyway.

### Setup steps to create the project from scratch:

install nvm (node version manager)
<br/>
https://github.com/coreybutler/nvm-windows/releases/download/1.1.12/nvm-setup.exe
```
> # steps to install nvm
> nvm install lts
> nvm use newest
> # verify both node and npm are active on your machine
> node -v 
> # should output the version
> npm -v
> # should output the version
> # in vscode...
> # navigate to the project directory.
> # Opening a terminal should put you there automatically.
> npm create vite@latest my-vue-app -- --template react
> npm install
> npm run dev
> # npm run dev will show us the default vite-react page. Use ctrl-c to stop it now that we know our project can launch. 
> # add sass to the project
> # create the dotnet project to the project directory
> # configure the connection details to the database and redis
```
### tip
<hr/>
You can setup an interface with an ip to map a local address other than localhost. IE: 172.10.0.20

You can update your hosts file to create an alias for your custom IP address.
<br/>IE: **myLearning.com 172.10.0.20**
<br/>so that you can navigate to 
<br/>**myLearning.com:5173/courses**

### Setup

- install vscode
- install git (vscode might install git for you)
- install docker (if you wish)
- install PostgreSQL if you dont plan on using a postgres docker image

Docker will create the interfaces needed to support mapping containers and handling their networking.


<b>Optional:</b>
<br/>
We can create a dockercompose file to generate a specific interface which exposes the routes to our host's interface.
<br/>
This will allow us to hit the container's ip address instead of using localhost.
<br/>The reason I use other ip addresses is to avoid conflicting services on localhost, as some might interfere with other containers, in case you/I have others running at the same time.