# Dennys Guide to making code look slightly better

Today, I will be going through our brand new eslintrc and prettierrc to make our code a little bit more ledgable. First, We will start with Prettier.

In your VSCode Extensions, please install prettier. What this does is whenever you save your code, this will follow some rules to format in a specified way. You can adjust this with .prettierrc.js, as those contain rules for prettier to follow towards.

In your settings, make sure to enable formatOnSave, or if you are using settings.json, paste this into there.

```json
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true
    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true
    },
    "[javascriptreact]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true
    },

```

This will automatically format your html, javascript, and react code.

Next, for ESlint, you will want to install it as a dev dependancy. Here are my following dev dependancies:

```json
	"devDependencies": {
		"eslint": "^6.8.0",
		"eslint-config-prettier": "^6.10.0",
		"eslint-plugin-prettier": "^3.1.2",
		"nodemon": "^2.0.3",
		"prettier": "^1.19.1"
	}
```

Next up, copy over the .eslintrc.json into the main directory of your code. (Typically, where your package.json would be.)

ESlint is a set of rules that the code will throw errors on if you break, such as using double quotes instead of single quotes, or mixing quotes in general. This will mark errors in our code wherever we "break" a rule.

But, you might ask, that takes forever to fix, how can I automate this? Well, luckily eslint can actually handle all of that for you.

There are 2 possible ways, the first way, is if you have eslint installed, you can run eslint (path to file) --fix, and depending on the rules, will automatically fix the code for you. Prettier will also try to make these fixes for you as well, but can sometimes miss.

The second way is to implement a script in your package.json. You can add the following:

```json
"lint":"eslint ./targetFolder --fix"
```

In order to target a specific set of files. This will go through and automatically run and fix the linter for you. Be careful, this does have a chance of breaking your code, but it has a failsafe of exiting with an error code if that does end up happening.

One other file I have in here is the .eslintignore, which essentially lets eslint know which files to ignore. In my case, I ignore CSV files, as I really don't want to format those.

Lastly, .editorconfig is just a configuration for your editor, this should match your prettierrc. I like to have it just in case.

## What do you do with all this stuff?

All you have to do is paste all of this (excluding the README.md) into your project, and it should just work. Make sure you do have prettier enabled on save, and you should see errors. If not, check output and it might tell you your problem. One issue I had was that eslint couldn't find a target, and I had to go insert a specific path into my settings so that it would check for the eslint config in there.

Credits to Caleb for letting me use his linter :)