# Node.js / Express / TypeScript Setup Guide

A beginner's guide to setting up a TypeScript project with Node.js, Express, CORS, and Nodemon.

## Setup instructions

1. Create a new project folder and navigate to it:

```
mkdir my-nodejs-express-project
cd  my-nodejs-express-project

```

2. Initialize a new Node.js project:

```
npm init -y

```

3. Install TypeScript and required dependencies:

```
npm install typescript ts-node @types/node --save-dev

```

4. Generate TypeScript configuration file:

```
npx tsc --init

```

5. Create the project structure:

```
mkdir src
mkdir dist

```

6. Configure TypeScript

```
{
"compilerOptions": {
"target": "es6",
"module": "commonjs",
"rootDir": "./src",
"outDir": "./dist",
"strict": true,
"esModuleInterop": true,
"skipLibCheck": true,
"forceConsistentCasingInFileNames": true
},
"include": ["src/**/*"],
"exclude": ["node_modules"]
}

```

7. Install Express, CORS, and their type definitions:

```
npm install express cors
npm install @types/express @types/cors --save-dev

```

8. Install Nodemon for development (hot reload):

```
npm install nodemon --save-dev

```

and create file ```nodemon.json```

```
{
  "watch": ["src"],
  "ext": ".ts,.js",
  "ignore": [],
  "exec": "ts-node ./src/index.ts"
}

```

9. Set Up package.json Scripts

```
{
    "scripts": {
    "start": "node dist/index.js",
    "dev": "nodemon src/index.ts",
    "build": "tsc"
    }
}

```

10. Create your first express app in Typescript

```
import express from "express";
import cors from "cors";

const app = express();


app.use(cors());
app.use(express.json())

app.get("/", (req, res) => {
  res.send("Node.js and Express.js with TypeScript");
});

app.listen(3000, () => {
  console.log("Server is running on port 3000");
});


```
