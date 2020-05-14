# Component and Props

In this section we will learn about how you can organise React Nodes to form Components that will act as a building block of any app.

Components lets you breakdown you app into independent, reusable chunks of UI. You can think of components to be a reusable chunk of HTML.

Say for example if we have to break down a layout in small small components. This is how you should think.

![Component Breakdown](/Users/ankit/Documents/work/js_altcampus/react-docs/component-and-props/assets/break-down.png)

You can think of a layout to be a collection of small small different components. Like the layout consists of the followinf components:

- Header
- Hero Section
- Articles
  - Article
- Footer

If you look at the articles component, it is a collection of 6 different article component.

#### How to create a component

Say we want to create Article box that consists of a image and a title.

```jsx
let article = (
  <React.Fragment>
    <img src="https://images.unsplash.com/photo-1498837167922-ddd27525d352?w=300" />
    <h3>Third Halving Turns Out to Be Non-Event for Bitcoin’s Price</h3>
  </React.Fragment>
);
```

All 6 different article consists of different informations like for each article the image url and title will change to how can we re-use this. To use the same thing multiple time in JavaScript we can convert this into function and pass those information as parameter like

```js
let article = articleInfo => (
  <React.Fragment>
    <img src={articleInfo.url} />
    <h3>{articleInfo.title}</h3>
  </React.Fragment>
);
```

Now we can call above function multiple times with multiple parameter. So, a function that returns a React element is called as a component. You need to name a component in React starting with capital case so it should not be `article` it should be `Article`.

Babel converts your JSX into JS by calling:

- For elements like p, div, span `React.createElement('p')` (p is as string)
- For components it is like `React.createElement(Article)` (Article as variable)

Making the name of component capital case helps babel to call component as varibale. Otherwise if Article will be called a sstring and that will not work properly. Play around to see the difference between `Article` and `article` [link](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&spec=false&loose=true&code_lz=GYVwdgxgLglg9mABAQQE6wgGwKYAoCUA3gFACQq2UIqSAPABYCMAfGhjrQPRPPEC-xYqEiwEiAIboYWPETIUqNRAxZtpHbi36DaAExgA3XomU8AEtkyY4iAFIBlABoBCLj2InaamYk7HlkuzYvrxc-kaCQA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2%2Cenv&prettier=false&targets=&version=7.9.6&externalPlugins=)

You can call the component in JSX like `<Article />` instead of `Article()`. Calling it like `<Article />` make it look similar to HTML element. To Send arguments to the component you can pass it like how you pass attributes to HTML like `<Article url="https://hello.com/img" title="Best article in town.">`

Below we have two objects with different information and we can call the article

```html
<html>
  <body>
    <div id="root"></div>
    <script src="https://unpkg.com/react@16.13.1/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@16.13.1/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone@7.8.3/babel.js"></script>
    <script type="text/babel">
      let firstArticleInfo = {
        url:
          'https://www.coindesk.com/third-blockchain-halving-turns-out-non-event-bitcoins-price',
        title: 'Third Halving Turns Out to Be Non-Event for Bitcoin’s Price',
      };
      let secondArticleInfo = {
        url:
          'https://www.coindesk.com/third-blockchain-halving-turns-out-non-event-bitcoins-price',
        title:
          'Gibraltar Financial Services Minister Talks ‘Staying Ahead’ on DLT',
      };
      let Article = articleInfo => (
        <React.Fragment>
          <img src={articleInfo.url} />
          <h3>{articleInfo.title}</h3>
        </React.Fragment>
      );
      let articles = (
        <React.Fragment>
          <ArticleInfo
            url={firstArticleInfo.url}
            title={firstArticleInfo.title}
          />
          <ArticleInfo
            url={secondArticleInfo.url}
            title={secondArticleInfo.title}
          />
        </React.Fragment>
      );
      ReactDOM.render(heading, document.getElementById('root'));
    </script>
  </body>
</html>
```
