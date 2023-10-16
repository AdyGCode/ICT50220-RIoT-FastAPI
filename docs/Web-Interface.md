# Web Interface

To create a web interface using FastAPI is easy enough as we use a templating engine to do so.

In our case we will use Jinja2 for templating.

Wew will also use the TailWindCSS CSS framework, so we will need NodeJS installed.

## Setting Up

1. Create the following folders:
   1. `templates`,
   2. `static`,
   3. `data`, and 
   4. `src` 
```shell
mkdir templates static src data
```
2. Install NodeJS if you have not done so
3. Make sure you are able to run Node from within your Python Project (run the following to see if you get a version number back - if not try exiting PyCharm and reopening once you have installed NodeJS and made sure it is the path.)
```shell
node -v
```
4. Install TailwindCSS and initialise the project 
```shell
npm install -D tailwindcss
npx tailwindcss init
```
5. Add the required paths to the tailwind.config.css 
```js

```
5. Create a file `src\input.css` and add the following
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
7. Open a new terminal and execute the "watch and compile" scripts - this will continuously build the styles
```shell
npx tailwindcss -i ./src/site_input.css -o ./static/site.css --watch
```
8. Go back to the first terminal, ready for later.
9. Create a new file, `templates\index.html`, add the following code: