# When to use react-snap

React-snap pre-renders your client-side javascript web app into static html in order to improve first-time paint, which drastically helps with SEO scores, and also increases overall performance.

Some of the other approaches to achieve similar results are more thoroughly discussed by this project's author [here](https://github.com/stereobooster/react-snap/blob/master/doc/anatomy-of-js-static-website-generator.md).

Let's discuss whether or not react-snap is the solution you are looking for to bring some of the benefits listed above to your project:

React-snap converts the dynamic javascript into static html and then you serve these files directly from your web server as entrypoints. The app needs to hydrate soon after being rendered though, in order to provide the full functionality to the users.

Instead of using react-snap, you could build a fully SSR application using a framework such as [NextJS](https://github.com/vercel/next.js/) which provides a set of sophisticated and configurable rendering strategies for you to use on scalable and complex applications.

You could also use a static site generator such as [Gatsby](https://github.com/gatsbyjs/gatsby) or maybe [React-static](https://github.com/react-static/react-static) in order to pre-render your pages and fetch your data at build time, preparing a fully working app for your clients in several configurable ways of generating web pages.

When comparing react-snap to both of the possibilities listed above, here is a list of things you should consider:

## Upsides

* React-snap is much easier to implement on legacy applications, since it required zero configuration
* As listed above, you shouldn't spend too much time because it doesn't require too much configuration for the common use case
* Developer experience is pretty much the same as "regular" client-side (such as create-react-app)
* Significant SEO and performance gains for a very low effort
* Works on any kind of web app, doesn't bind you to any framework
* Uses a Headless browser, which provides a more similar environment to the client-side than other approaches such as `renderToString` or `JSDOM`

## Downsides

* Might increase your web server's complexity since additional configuration might be needed to properly serve the HTML entrypoints
* You might need to write specific code to exclude client-side only logic
* The larger and more complex your application grows, the more difficult it may get to properly manage the pre-rendered parts
* It isn't the best approach for when you need to fetch dynamic data at build time
* Limits your flexibility when it comes to advanced SEO techniques sometimes, even though this can be dealt with additional tooling

## Conclusion

This approach is best suited when you don't want to move away from the "regular" client side development experience, and only need a bit of improvement over regular SPAs that are way too slow for modern SEO requirements and whatnot. React-snap allows you to achieve awesome optimizations with very low effort. You can also take a look at other easy optimization techniques drafted by @stereobooster [here](https://github.com/stereobooster/react-snap/blob/master/doc/an-almost-static-stack-optimization.md).

If you are looking to build an application from scratch that needs to take advantage of sophisticated performance advantages and grow on unexpected ways, I believe you would be better suited with another approach.

If the pre-rendered parts of your app require a lot of dynamic data fetching, it may also be a problem, and you may need to dive deeper into react-snap and customize it into your use case to make it work.

It may also be problematic to make it work properly with some CDNs such as Cloudfront + s3, some people ended up having to configure Lambda@Edge functions in order to properly take benefit of react-snap, which might not be what you're looking for.

At the same time, it seems to work flawlessly with Firebase Hosting, for instance. Take a look around at the original repository's [issues](https://github.com/stereobooster/react-snap/issues) to get an idea of how well it works with your setup.

The ideal use case for react-snap should be an existing app that needs SEO and performance improvements without the need to dive into the code and make changes there. If you don't want to spend too much time on optimization, this is definetely worth looking into. If you want to invest heavily, it might be better to consider more complex options such as the static site generators and SSR frameworks listed above.
