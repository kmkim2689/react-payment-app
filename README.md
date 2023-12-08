# Bank App

## Reference
[Build and Deploy a Fully Responsive Website with Modern UI/UX in React JS with Tailwind](https://youtu.be/_oO4Qi5aVZs?feature=shared)

## Project Setup

### Initialization
* Not using `create-react-app`, but using `Vite`
    * Compared to create-react-app, Vite is much faster to create a react app
    * https://ko.vitejs.dev/guide/

* Procedure
1. In terminal, type this line below:
```
npm create vite@latest
```

2. Set the name of the project

3. Choose the library(React, Vue...)

4. Set the language(for react, js or ts)

5. **Move to the Project Root Folder**, then Type this line below to install all of the needed dependencies
```
cd name_of_the_project_root_folder
```
```
npm install
```

6. Try the starter app that was set in advance by vite
```
npm run dev
```
* the url of the local host appears, click the link with `Ctrl`
```
  ➜  Local:   http://localhost:5173/ // click with Ctrl
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
```

* Advantages of Vite
    * App initializing is much faster
    * Minimal Configuration
        * App.css, App.jsx, index.css, main.jsx => only 4 defualt files


### Setup Tailwind CSS
* As the project is initialized with Vite, the installation of Tailwind CSS should be done using `PostCSS`, compared to create-react-app
    > Installing Tailwind CSS as a PostCSS plugin is the most seamless way to integrate it with build tools like webpack, Rollup, Vite, and Parcel.
    * https://tailwindcss.com/docs/installation/using-postcss

1. type the line below on the terminal
```
npm install -D tailwindcss postcss autoprefixer
```
```
npx tailwindcss init -p // without -p, 'postcss.config.js' does not generate automatically
```

2. Set up `tailwind.config.js`
* add colors, fontFamily, screen sizes to easily reference on the codes
```
/** @type {import('tailwindcss').Config} */

module.exports = {
  content: ["./index.html", "./src/**/*.{js,jsx}"],
  mode: "jit",
  theme: {
    extend: {
      colors: {
        primary: "#00040f",
        secondary: "#00f6ff",
        dimWhite: "rgba(255, 255, 255, 0.7)",
        dimBlue: "rgba(9, 151, 124, 0.1)",
      },
      fontFamily: {
        poppins: ["Poppins", "sans-serif"],
      },
    },
    screens: {
      xs: "480px",
      ss: "620px",
      sm: "768px",
      md: "1060px",
      lg: "1200px",
      xl: "1700px",
    },
  },
  plugins: [],
};
```

3. Add the @tailwind directives for each of Tailwind’s layers to your `main`(index) CSS file.
* index.css : where we want to make use of tailwind
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

* styles needed for the app in index.css
```
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800;900&display=swap");

:root {
  --black-gradient: linear-gradient(
    144.39deg,
    #ffffff -278.56%,
    #6d6d6d -78.47%,
    #11101d 91.61%
  );
  --card-shadow: 0px 20px 100px -10px rgba(66, 71, 91, 0.1);
}

* {
  scroll-behavior: smooth;
}

.text-gradient {
  background: radial-gradient(
    64.18% 64.18% at 71.16% 35.69%,
    #def9fa 0.89%,
    #bef3f5 17.23%,
    #9dedf0 42.04%,
    #7de7eb 55.12%,
    #5ce1e6 71.54%,
    #33bbcf 100%
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
}

.bg-blue-gradient {
  background: linear-gradient(
    157.81deg,
    #def9fa -43.27%,
    #bef3f5 -21.24%,
    #9dedf0 12.19%,
    #7de7eb 29.82%,
    #5ce1e6 51.94%,
    #33bbcf 90.29%
  );
}

.bg-black-gradient {
  background: linear-gradient(
    144.39deg,
    #ffffff -278.56%,
    #6d6d6d -78.47%,
    #11101d 91.61%
  );
}

.bg-black-gradient-2 {
  background: linear-gradient(
    -168.39deg,
    #ffffff -278.56%,
    #6d6d6d -78.47%,
    #11101d 91.61%
  );
}

.bg-gray-gradient {
  background: linear-gradient(
    153.47deg,
    rgba(255, 255, 255, 0) -341.94%,
    #14101d 95.11%
  );
}

.bg-discount-gradient {
  background: linear-gradient(125.17deg, #272727 0%, #11101d 100%);
}

.box-shadow {
  box-shadow: 0px 20px 100px -10px rgba(66, 71, 91, 0.1);
}

.sidebar {
  -webkit-animation: slide-top 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  animation: slide-top 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

@-webkit-keyframes slide-top {
  0% {
    -webkit-transform: translateY(100px);
    transform: translateY(100px);
  }
  100% {
    -webkit-transform: translateY(0);
    transform: translateY(0);
  }
}

@keyframes slide-top {
  0% {
    -webkit-transform: translateY(100px);
    transform: translateY(100px);
  }
  100% {
    -webkit-transform: translateY(0);
    transform: translateY(0);
  }
}

.feature-card:hover {
  background: var(--black-gradient);
  box-shadow: var(--card-shadow);
}

.feedback-container .feedback-card:last-child {
  margin-right: 0px;
}

.feedback-card {
  background: transparent;
}

.feedback-card:hover {
  background: var(--black-gradient);
}

.blue__gradient {
  background: linear-gradient(180deg, rgba(188, 165, 255, 0) 0%, #214d76 100%);
  filter: blur(123px);
}

.pink__gradient {
  background: linear-gradient(90deg, #f4c4f3 0%, #fc67fa 100%);
  filter: blur(900px);
}

.white__gradient {
  background: rgba(255, 255, 255, 0.6);
  filter: blur(750px);
}
```

4. Delete App.css file, Delete all the contents in App.jsx and replace it with:
```
// rface
import React from 'react'

const App = () => {
  return (
    <div>App</div>
  )
}

export default App
```

5. add the image files needed for the app in `assets` folder:
* src > assets

6. add the constants(objects) for using text/links as variables
* src > constants > index.js
* to avoid hard-coded texts