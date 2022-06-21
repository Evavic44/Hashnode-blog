## Three Awesome Ways to Install & Set up SASS

Knowing what compiler to use for your SASS project can be daunting to decide on because there are numerous apps and extensions for doing that, so I'll be sharing with you three awesome ways you can install and get <a href="https://sass-lang.com/" target="_blank">SASS</a> up and running in your projects.

## Prerequisites
- Basic knowledge of HTML
- Basic knowledge of CSS

## What is SASS
SASS is a CSS preprocessor/precompiler that enhances the functionality of CSS. It has awesome features that help make writing CSS a lot smarter and easier. SASS stands for "syntactically awesome style sheet".

## How does SASS work?
Sass uses `.scss` or `.sass` file extensions, but `.scss` is by far the most popular.
The browser does not read SASS files directly, they must be compiled to CSS, and there are many programs for compiling SASS files to CSS which we'll be discussing in this article. 

This article uses the `.scss` syntax because it is widely used and easier to work with. But you can go with the `.sass` extension and syntax if you want.


### Edit on (Jan 02, 2022)

On Oct 26, 2021, The SASS core team released major updates to the SASS language, which deprecated LibSass, Node Sass, and SassC. In this edit, I'll be sharing the updated and recommended way of setting up Sass in your project.

%[https://twitter.com/SassCSS/status/1320820104561524736?s=20]


### Step i. Install SASS globally.

The first step is to install SASS globally. To do that, run the following command in your terminal.

```js
npm install -g sass
```

If you run into any errors, try adding **sudo** as a prefix.

```js
sudo npm install -g sass
```

This will install dart sass globally from NPM.

### Step ii. Create our directories

The next step is to create our SCSS folder and file along with our CSS folder.
You can do that in the command line or just create the folders natively on your PC.
To do that in the command line, type the following:

```js
mkdir scss
```

Where **mkdir** stands for "make directory", so we're saying create a folder or directory called scss. Now add your sass file inside this scss directory.

Run the same command but this time for the CSS. 

```js
mkdir css
```

We don't have to create a css file because once we save the changes in our SASS file, it'll automatically create the css file for us.

### Step iii. Watch SASS
Now we have created our directories, we need to activate the watch flag to watch the SCSS folder and compile any changes to CSS. 

```js
sass --watch scss:css
```

Now you can see the output in the command line that says **Sass is watching for changes. Press Ctrl-C to stop.**

![dart-sass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1641077129899/iE2uPuCAq.png)

This command will constantly watch the **SCSS** folder and compile any changes we make to **CSS**

For some, your project may be structured differently by having the **css** folder inside a **dist** folder or any other way you may want it to be. If that is the case, you can use a forward slash to target the css folder within a parent directory(dist in this case) like so:

```js
sass --watch scss:dist/css
```

Of course, for this to work, your css folder must be in the dist directory. 🙃

Finally, we have successfully gotten SASS up and running in our projects using **Dart SASS** Let's test it out.

![dart-sass-compiled.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1641081307287/JLo90gg1e.png)

We can see a success message that says **Compiled scss\main.scss to css\main.css.**

## Installation of Dart SASS locally

You can also install Dart SASS into your machine by downloading one of their <a href="https://github.com/sass/dart-sass/releases/tag/1.45.1" target="_blank">packages</a> and adding it to a path folder in your machine. You can read more on how to do that <a href="https://gist.github.com/nex3/c395b2f8fd4b02068be37c961301caa7#file-path-md" target="_blank">here</a>. Available for Windows, Mac, and Linux.

## Why Dart SASS?

Dart Sass has replaced Ruby Sass as the canonical implementation of the Sass language. We chose Dart because it presented a number of advantages. <a href="https://github.com/sass/dart-sass#why-dart" target="_blank">Read more</a>

Below are other ways of setting up SASS in your project, though <a href="https://sass-lang.com/blog/libsass-is-deprecated">deprecated</a>, still worth checking out. 👇🏾


## 1. Environment Setup With Node SASS

![node-sass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640357313284/dYLdh315i8y.png)

This is one of the first methods we'll be discussing. This involves installing sass using the <a href="https://www.npmjs.com/" target="_blank">node package manager(NPM)</a>, coupled with a simple NPM script that watches a certain folder where we created our sass files and complies it to regular CSS in the folder we specified. 

<img src="https://media3.giphy.com/media/glmRyiSI3v5E4/giphy.gif?cid=ecf05e4765yzuehgn07bhuimj1iqn5mmllci19jr2njt3ucm&rid=giphy.gif&ct=g" alt="Picture of Tom Cruise expressing confusion">

Sounds like mumbo jumbo? 😅 don't worry, it'll make more sense as we go.

### Step i. Download and install node
In other to use NPM to install sass, we have to download and install node into our PC. Visit <a href="https://nodejs.org/en/" target="_blank">Nodejs</a> official website to download it. You can choose whichever version of node you would like to install, it doesn't matter in this case. I went with the long-term support version(LTS), but either one works.

![node.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640077892588/BLVD7zlEo.png)

If you already have node installed, skip this step. 

Now we're done downloading and installing node into our PC, to check if it was installed properly, open up your terminal or command line and type in `node --version`, and hit enter. This should give us the version of node currently installed.

![node-version.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640101905491/nteDDZdNr.png)

### Step ii. Create a package.json file
Since we're installing anything from NPM, we'll need to create a `package.json` file.

To do that, type the following command in your terminal.

```js
npm init -y
```

The `-y` flag is used to skip any questions NPM will ask you and create the `JSON` file with the default settings.
 
This command will create our `package.json` file in the project folder, using the default settings.

![create-a-package.json-file.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640104070410/6yUhiUIRr.png)

### Step iii. Install Node-sass
Now we have created our `package.json` file, we can install Node SASS which will install SASS in the `node-modules` folder, and add it as a dependency in the `package.json` file. 

To install Node SASS, type the following command.

```js
npm install node-sass
```

![node-modules.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640110248987/qIqmkwo76.png)

Now we have successfully installed node-sass in the `node_modules` folder and it is also added as one of the dependencies in the `package.json file`. 

### Step iv. Create an NMP script to run SASS
The next step is to create an NPM script that will allow us to use SASS in our project. To do that, modify

this line:

```js

"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },

```

and change it to:

```js

"scripts": {
    "sass": "node-sass -w scss/ -o dist/css/ --recursive"
  },

```

![npm-script.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640111751995/l79kpmJBv.png)

*Here's what it looks like in our editor.* 

So let's go over this new script we added and explain what it does in detail.

- Node-sass: This is saying run sass.
- `-w` is a watch flag that watches for an SCSS folder (You can name this folder anything you want, but this is where our SASS files will be saved.)
- `-o dist/css/ --recursive` is simply saying, output the compiled SASS code into a dist/css/ folder.

This is a basic page structure of our SASS project, you might choose to structure your project differently, don't forget to update it in your `package.json` file.

### Step v. Create our respective folders and files
This next step is to create the appropriate files and folders for our SASS project, which will follow the page structure in the `package.json` file.

- Create two folders: dist, and scss
- Inside the dist folder, we'll have our HTML file, and CSS folder.
- And then finally, our `main.scss` file.


![Node SASS folder structure](https://cdn.hashnode.com/res/hashnode/image/upload/v1640371894181/8BrV4RV2A.png)

### Step vi. Start SASS
After successfully creating the required folders, run the following command to start SASS.

```js
npm run sass
```

This command will constantly watch the SCSS folder and any changes made to the SASS file will be compiled immediately to CSS in the dist folder.

Let's write some code to test this out.

```scss
// sass variable 
$color: red;

body {
  background: $color;
}
```
 
And when we hit save, we get a success message on the command line that says: **rendering complete, saving .css file** which means our sass file will be compiled to regular CSS and give the desired output, which is a red background.

![output-sass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640274650838/37daLvyYa.png)

So that's how you set up SASS using NPM.

### Issues with Node SASS

<img src="https://media3.giphy.com/media/QajHhLKW3VRcs/giphy.gif?cid=ecf05e473qm1k7lgge85ya8v0akq15zz3qdbg6t841a33o98&rid=giphy.gif&ct=g" alt="Man showing disappointment">

If you are using Node Sass in VS code, you might come across this <a href="https://github.com/sass/node-sass/issues/2022">issue</a> that prompts an error in the command line when you save your changes:

```js
Error: Unrelated file
Message: File to read not found or unreadable:
"formatted": "Internal Error: File to read not found or unreadable:
```
 
When this error happens, the changes you made at that time won't be compiled, you will have to keep hitting save until it shows success. 

I took the liberty of researching about this error, and luckily, I found a patch that works just right for it. 
You can read more about it and how to fix it here.

%[https://github.com/sass/node-sass/issues/1894#issuecomment-390199128]

Too lazy to do that, locate the file `node-sass/lib/render.js` inside your local `node_modules` folder and replace it with this code: https://github.com/marcosbozzani/node-sass/blob/bug-vscode-watch/lib/render.js

That's it for Node Sass. Now let's look at other awesome ways.


## 2. Installation using Koala GUI Compiler 

![koala.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640358940068/xHzuRYVA4.png)

<a href="http://koala-app.com/" target="_blank">Koala</a> is a Graphic User interface(GUI) application for compiling files like `SASS`, `LESS`, `Compass`, `CoffeeScript`, ETC.
If Node-sass was tedious to set up and use, you can check out this GUI tool that allows you to set up sass just by clicking some buttons. 

![koala.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640281711065/SbEZSH6QF.png)

### Step i. Install Koala GUI
To install Koala, visit their website <a href="http://koala-app.com/" target="_blank">Koala-app.com</a> and download it into your machine. It is available for Windows, Mac, and Linux.
So download and install it.

### Step ii. Create the respective files and folders.
Create a new project folder and inside, we'll have our scss and dist folder.
- Inside the SCSS folder, create a new file called `main.scss`. You can name this whatever you want as long as it has a file extension of `.scss`
- Inside the dist folder, we'll have our index.html file and CSS folder which contains our main.css file. 

### Step iii. Add project folder to Koala
There are two ways to add a project to Koala, you can do a simple drag and drop into Koala or add the project using the plus sign on the top.

If you're adding through the plus sign, locate the project folder and select it.

Once we add the project folder to Koala, it will automatically compile the `SASS` file to `CSS`. 

By default, the compiler will put the `CSS` file in the same folder as the SCSS file, along with a `css.map` file. If you don't like that, you can direct it to go into the CSS folder in the dist by
- Right-clicking on the `scss` file and select **Set output path** 

![koala-set-output-path.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640280955673/TSZDqbpEX.png)

this will prompt open a folder, locate the `main.css` file inside the dist folder, select it and then hit save.

Now you can delete the `main.css` and `main.css.map` files in the SASS folder since we changed the folder structure.

![koala-delete-css-files.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640280803675/S2dOjUhZE.png)

To compile to the new folder, click on the SASS file in Koala and click **compile** You can also turn on **auto compile** so that when we save, it'll automatically get compiled to `CSS`.

![koala-auto-compile.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640280347735/W-o7CA5Tg.png)

## 3. Live SASS VS Code Extension

<img src="https://github.com/ritwickdey/vscode-live-sass-compiler/blob/master/images/icon2.png?raw=true" alt="Live Sass logo">

<a href="https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass" target="_blank">Live SASS</a> is an awesome extension by <a href="https://github.com/ritwickdey/" target="_blank">@ritwickdey</a>(author of <a href="https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer" target="_blank">Live Server</a>) for compiling SCSS/SASS files at realtime with live browser reload.. It is super easy to use and set up. If you're using VS Code, I strongly suggest you check it out.

### Step i. Download & Installation

![live-sass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640290267421/Oz5lfDNoD.png)

You can download live sass from visual studio code extensions or <a href="https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass" target="_blank">marketplace</a> online.

- Open up the extensions tab on VS Code and search for live sass. Install it into your PC. 
- Once Live Sass is successfully installed, you should see a button on the bottom of your editor that says **Watch Sass**. 

![watch-sass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640453872915/CuIt0Rpz3L.png)

If you click this button, it'll compile your SASS file to CSS in the same folder. So let's look at how we can configure this.

### Step ii. Configuration
Just like Koala GUI, you can specify the output folder you want the CSS file to be saved in.
- Go to your VS Code settings and search for live sass.
- Click edit in **settings.json** 

![settings-json.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640364716263/wFMuqgLtu.png)

- Inside the settings.json file, scroll to the line that says: `savePath: null` and edit it with the directory you want your CSS file to be saved in. If you don't have this line, you can copy this code below and paste it into your `settings.json` file. 

**Code Sample**

```js
   "liveSassCompile.settings.formats": [
    {
      "format": "expanded",
      "extensionName": ".css",
      "savePath": "/dist/css/"
    }
  ],
"liveSassCompile.settings.generateMap": false,
```

- On the `savePath: null` command, we're targeting a folder called css inside the dist folder.
- The `liveSassCompile.settings.generateMap` is used to toggle the CSS map file from showing, when we compile our SASS file. The default value is `true`, set it to `false` if you want it to be hidden.
- Save and exit the `settings.json` file. 
- Click the **watch sass** icon and when we hit save, it should compile to the newly specified folder. 

![live sass compiler success message.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640365661225/ojM3NOPcA.png)

**Tip:** This setting will persist for any SASS project in VS code, so you don't need to do this for every project. 

# Final Words
Installing and setting up SASS for the first time might be a bit challenging, so it's okay to keep referring back to this article from time to time. 💯 And like anything you're learning, it'll become easier with time. 
While following this article, If you ran into any issues, check to see if you linked your CSS file properly to the HTML and If you're using Node SASS, make sure Node sass is running to avoid smashing your computer to a wall, I know I almost did. 🥲

Also, it's good to remember that these are not the only ways you can install and compile SASS to CSS. There are other software, though mostly paid, that are available to use. You can read the <a href="https://sass-lang.com/install">SASS documentation</a> for more info on that.

# Important links to checkout
- <a href="https://sass-lang.com/documentation">SASS Documentation</a> 
- <a href="https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass&ssr=false#overview">Live SASS extension</a>
- <a href="https://github.com/sass/node-sass">Node SASS repository</a>
- <a href="https://eke.hashnode.dev/i-built-hashnodes-landing-page-clone-with-sass">Hashnode clone with SASS</a>

Thanks for reading, have any questions or contributions, you can leave them in the comments below. I'll be releasing another article on how to use SASS shortly, so be on the lookout for that. In the meantime, keep coding and don't let the error bugs bite. 