<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<div align="center">

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

</div>


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/Nalipas/Book-Search-Engine">
    <img src="https://media.tenor.com/q1A3UVgCQC0AAAAi/pepega-reading.gif" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Book Search Engine</h3>

  <p align="center">
    A full stack application using Google Books Search API.
    <br />
    <a href="https://github.com/Nalipas/Book-Search-Engine"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/Nalipas/Book-Search-Engine">View Demo</a>
    ·
    <a href="https://github.com/Nalipas/Book-Search-Engine/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
    <a href="https://github.com/Nalipas/Book-Search-Engine/issues/new?labels=enhancement&template=feature-request---.md">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#root-level-functionality">Root Level Funcitonality</a></li>
        <li><a href="#client-side-functionality">Client Side Funcitonality</a></li>
        <li><a href="#server-side-functionality">Server Side Funcitonality</a></li>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot]](https://example.com)

The Berkeley Extension Coding Bootcamp Alumni Center is a web application which acts as a social network for Alumni of the Coding Bootcamp hosted at the UC Berkeley Extension. Here, Alumni can connect by sharing their experiences and contact information with each other through user profiles and thought posting.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With

* [![React][React.js]][React-url]
* [![Vite][Vite.js]][Vite-url]
* [![Express][Express.js]][Express-url]
* [![Graph][GraphQL]][GraphQL-url]
* [![Mongo][MongoDB]][MongoDB-url]


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

This is an example of how to get the project running on your local machine. Alternatively, the application is hosted on Render(LINK).

### Root-level Functionality

* The `npm start` script: In production, we only run the back-end server, which will serve the built React application code as its front end.

* The `npm run develop` script: In development, we need to run both a back-end server and the React development server, so we use the `concurrently` library to execute two separate promises at the same time.

* The `npm install` script: Since our dependencies for the entire application exist in two smaller applications, we use this script to automatically install all of them at once.

* The `npm run seed` script: We can seed our database with data when we run this command.

* The `npm run build` script: When we deploy our application, we instruct the hosting service to execute the `build` command and build our production-ready React application."

```json
"scripts": {
  "start": "node server/server.js",
  "develop": "concurrently \"cd server && npm run watch\" \"cd client && npm run dev\"",
  "install": "cd server && npm i && cd ../client && npm i",
  "seed": "cd server && npm run seed",
  "build": "cd client && npm run build"
},
```

### Client-side Functionality

* Since we run a front-end and back-end server for our full-stack application in development, we set it up so all client-side requests to our API server are prefixed with the API server's URL.

```js
  proxy: {
    '/graphql': {
      target: 'http://localhost:3001',
      changeOrigin: true,
      secure: false,
    },
  },
```

### Server-side Functionality

* In production, when we no longer need to use the `vite` development server; we set up our server to serve the built React front-end application that is in the `../client/src` directory.

* Since the React front-end application will handle its own routing, we set up a wildcard route on our server that will serve the front end whenever a request for a non-API route is received.

```js
if (process.env.NODE_ENV === 'production') {
  app.use(express.static(path.join(__dirname, '../client/src')));
  
  app.get('*', (req, res) => {
    res.sendFile(path.join(__dirname, '../client/src/index.html'));
  });
}
```

### Prerequisites

<a href="https://nodejs.org/en/download/package-manager">Node.js</a> and <a href="https://docs.npmjs.com/downloading-and-installing-node-js-and-npm">Node Package Manager (NPM)</a> are required to download and install the dependencies of this project. Install <a href="https://nodejs.org/en/download/package-manager">Node.js</a>, then run this command in your CLI to install NPM.
* npm
  ```sh
  npm install -g npm
  ```

### Installation

1. Clone the repo to your desired directory.
   ```sh
   git clone git@github.com:Nalipas/Book-Search-Engine.git
   ```
2. Install NPM packages
   ```sh
   npm run install
   ```
3. Seed the database.
    ```sh
    npm run seed
4. Run the application.
    ```sh
    npm run start
<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

The application can be run locally, or in your browser.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Steven Moreno - [@Nalipas](https://github.com/Nalipas) - smoreno2014@gmail.com <br>

Project Link: [https://github.com/Nalipas/Book-Search-Engine](https://github.com/Nalipas/Book-Search-Engine)<br>
Deployed Project: [https://Book-Search-Engine.onrender.com/](https://Book-Search-Engine.onrender.com/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [Mark Carlson](https://github.com/mark-carlson) for instructor support
* [Mariah Wear](https://github.com/mariahw4) for TA support
* [Clarence C]() for TA support

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Nalipas/Book-Search-Engine.svg?style=for-the-badge
[contributors-url]: https://github.com/Nalipas/Book-Search-Engine/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Nalipas/Book-Search-Engine.svg?style=for-the-badge
[forks-url]: https://github.com/Nalipas/Book-Search-Engine/network/members
[stars-shield]: https://img.shields.io/github/stars/Nalipas/Book-Search-Engine.svg?style=for-the-badge
[stars-url]: https://github.com/Nalipas/Book-Search-Engine/stargazers
[issues-shield]: https://img.shields.io/github/issues/Nalipas/Book-Search-Engine.svg?style=for-the-badge
[issues-url]: https://github.com/Nalipas/Book-Search-Engine/issues
[license-shield]: https://img.shields.io/github/license/Nalipas/Book-Search-Engine.svg?style=for-the-badge
[license-url]: https://github.com/Nalipas/Book-Search-Engine/blob/master/LICENSE.txt
[product-screenshot]: images/screenshot.png

[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vite.js]: https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=Vite&logoColor=white
[Vite-url]: https://vitejs.dev
[Express.js]: https://img.shields.io/badge/express-000000?style=for-the-badge&logo=express&logoColor=white
[Express-url]: https://expressjs.com
[GraphQL]: https://img.shields.io/badge/GraphQL-E434AA?style=for-the-badge&logo=graphql&logoColor=white
[GraphQL-url]: https://graphql.org/
[MongoDB]: https://img.shields.io/badge/-MongoDB-13aa52?style=for-the-badge&logo=mongodb&logoColor=white
[MongoDB-url]: https://www.mongodb.com
