# Installing Prefers Color Scheme

[Prefers Color Scheme] runs in all Node environments, with special instructions for:

| [Node](#node) | [PostCSS CLI](#postcss-cli) | [Webpack](#webpack) | [Create React App](#create-react-app) | [Gulp](#gulp) | [Grunt](#grunt) |
| --- | --- | --- | --- | --- | --- |

## Node

Add [Prefers Color Scheme] to your project:

```bash
npm install postcss css-prefers-color-scheme --save-dev
```

Use it as a [PostCSS] plugin:

```js
const postcss = require('postcss');
const prefersColorScheme = require('css-prefers-color-scheme');

postcss([
	prefersColorScheme(/* pluginOptions */)
]).process(YOUR_CSS /*, processOptions */);
```

## PostCSS CLI

Add [PostCSS CLI] to your project:

```bash
npm install postcss-cli css-prefers-color-scheme --save-dev
```

Use [Prefers Color Scheme] in your `postcss.config.js` configuration file:

```js
const prefersColorScheme = require('css-prefers-color-scheme');

module.exports = {
	plugins: [
		prefersColorScheme(/* pluginOptions */)
	]
}
```

## Webpack

_Webpack version 5_

Add [PostCSS Loader] to your project:

```bash
npm install postcss-loader css-prefers-color-scheme --save-dev
```

Use [Prefers Color Scheme] in your Webpack configuration:

```js
module.exports = {
	module: {
		rules: [
			{
				test: /\.css$/i,
				use: [
					"style-loader",
					{
						loader: "css-loader",
						options: { importLoaders: 1 },
					},
					{
						loader: "postcss-loader",
						options: {
							postcssOptions: {
								plugins: [
									[
										"css-prefers-color-scheme",
										{
											// Options
										},
									],
								],
							},
						},
					},
				],
			},
		],
	},
};
```

## Create React App

Add [React App Rewired] and [React App Rewire PostCSS] to your project:

```bash
npm install react-app-rewired react-app-rewire-postcss css-prefers-color-scheme --save-dev
```

Use [React App Rewire PostCSS] and [Prefers Color Scheme] in your
`config-overrides.js` file:

```js
const reactAppRewirePostcss = require('react-app-rewire-postcss');
const prefersColorScheme = require('css-prefers-color-scheme');

module.exports = config => reactAppRewirePostcss(config, {
	plugins: () => [
		prefersColorScheme(/* pluginOptions */)
	]
});
```

## Gulp

Add [Gulp PostCSS] to your project:

```bash
npm install gulp-postcss css-prefers-color-scheme --save-dev
```

Use [Prefers Color Scheme] in your Gulpfile:

```js
const postcss = require('gulp-postcss');
const prefersColorScheme = require('css-prefers-color-scheme');

gulp.task('css', function () {
	var plugins = [
		prefersColorScheme(/* pluginOptions */)
	];

	return gulp.src('./src/*.css')
		.pipe(postcss(plugins))
		.pipe(gulp.dest('.'));
});
```

## Grunt

Add [Grunt PostCSS] to your project:

```bash
npm install grunt-postcss css-prefers-color-scheme --save-dev
```

Use [Prefers Color Scheme] in your Gruntfile:

```js
const prefersColorScheme = require('css-prefers-color-scheme');

grunt.loadNpmTasks('grunt-postcss');

grunt.initConfig({
	postcss: {
		options: {
			processors: [
			prefersColorScheme(/* pluginOptions */)
			]
		},
		dist: {
			src: '*.css'
		}
	}
});
```

[Gulp PostCSS]: https://github.com/postcss/gulp-postcss
[Grunt PostCSS]: https://github.com/nDmitry/grunt-postcss
[PostCSS]: https://github.com/postcss/postcss
[PostCSS CLI]: https://github.com/postcss/postcss-cli
[PostCSS Loader]: https://github.com/postcss/postcss-loader
[Prefers Color Scheme]: https://github.com/csstools/postcss-plugins/tree/main/plugins/css-prefers-color-scheme
[React App Rewire PostCSS]: https://github.com/csstools/react-app-rewire-postcss
[React App Rewired]: https://github.com/timarney/react-app-rewired
