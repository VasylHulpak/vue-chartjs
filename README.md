# Vue 3 + TypeScript + Vite + ChartJS

Among many charting libraries for JavaScript application developers, Chart.js is currently the most popular one according to GitHub stars (~60,000) and npm downloads (~2,400,000 weekly).

Chart.js was created and announced in 2013 but has come a long way since then. It’s open-source, licensed under the very permissive MIT license , and maintained by an active community.

# Features
Chart.js provides a set of frequently used chart types, plugins, and customization options. In addition to a reasonable set of built-in chart types, you can use additional community-maintained chart types . On top of that, it’s possible to combine several chart types into a mixed chart (essentially, blending multiple chart types into one on the same canvas).

Chart.js is highly customizable with custom plugins to create annotations, zoom, or drag-and-drop functionalities to name a few things.

# Defaults
Chart.js comes with a sound default configuration, making it very easy to start with and get an app that is ready for production. Chances are you will get a very appealing chart even if you don’t specify any options at all. For instance, Chart.js has animations turned on by default, so you can instantly bring attention to the story you’re telling with the data.

# Integrations
Chart.js comes with built-in TypeScript typings and is compatible with all popular JavaScript frameworks including React , Vue , Svelte , and Angular . You can use Chart.js directly or leverage well-maintained wrapper packages that allow for a more native integration with your frameworks of choice.

# Developer experience
Chart.js has very thorough documentation (yes, you're reading it), API reference, and examples. Maintainers and community members eagerly engage in conversations on Slack , GitHub Discussions , and Stack Overflow where more than 11,000 questions are tagged with chart.js.

# Canvas rendering
Chart.js renders chart elements on an HTML5 canvas unlike several other, mostly D3.js-based, charting libraries that render as SVG. Canvas rendering makes Chart.js very performant, especially for large datasets and complex visualizations that would otherwise require thousands of SVG nodes in the DOM tree. At the same time, canvas rendering disallows CSS styling, so you will have to use built-in options for that, or create a custom plugin or chart type to render everything to your liking.

# Performance
Chart.js is very well suited for large datasets. Such datasets can be efficiently ingested using the internal format so you can skip data parsing and normalization. Alternatively, data decimation can be configured to sample the dataset and reduce its size before rendering.

In the end, the canvas rendering that Chart.js uses reduces the toll on your DOM tree in comparison to SVG rendering. Also, tree-shaking support allows you to include minimal parts of Chart.js code into your bundle, reducing bundle size and page load time.

![Alt text](image.png)
