## Debugging Next.JS

## What is Next.JS

[Next.JS](https://nextjs.org) is an amazing React framework created by [Vercel](https://vercel.com). It allows the developers to create Server-side, Client-side or Static websites. Unlike the other frameworks, the rendering in Next JS is **per page**. That means, the "about" page can be static, while the "home" page can be server-side. Next JS is on the rise, loved by the developers, and my favorite React framework so far.

> If you want to learn more about website rendering, read my other post [here](https://nikolovlazar.com/how-to-render-your-website).

## Environment

This article covers the debugging process using [Visual Studio Code](https://code.visualstudio.com/). You can use the same commands in other IDEs, but you need to write them in the specific format.

For simplicity, we will use [this repo](https://github.com/lazarnikolov94/debugging-nextjs) to show the debugging process. So, go ahead and clone it on your computer, execute `yarn install` and open it in Visual Studio Code.

## Debugging Next.JS

A Next.JS page has two parts: a server-side part and a client-side part. To debug both parts you will need two VSCode launch tasks. Let's dive in.

## Debugging the Server-side

The server-side code lives in the `getServerSideProps` method. It executes every time there's a request. To debug the server-side code we will need to add a new VSCode launch task. First, create a `.vscode` folder in the root of the project, and then inside that folder create a `launch.json` file. We will add our launch tasks here.

Inside the `launch.json` file add a new "Node: Launch Program" configuration. Then, you will need to add the following changes:

*   Remove the `skipFiles` property
*   Remove the `program` property
*   Add a new property `runtimeExecutable` with value `${workspaceFolder}/node_modules/.bin/next`

Your `launch.json` file should look something like this:

```json
{
    "configurations": [
        {
            "type": "pwa-node",
            "request": "launch",
            "name": "Next: Node",
            "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/next"
        }
    ]
}

``` 

That's it! Now open the `/pages/[owner]/[repo].tsx` file, add a breakpoint on line 32 and hit F5. When the Next.JS server starts navigate to [http://localhost:3000](http://localhost:3000) and click on one of the repos in the list. After clicking it, you should hit the breakpoint. Now you have the ability to inspect the `ctx` argument and the data received from GitHub's API.

## Debugging the Client-side

To debug the Client-side first you need to install the [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome) extension. Open the link and click on the Install button. It will ask you to open the link in Visual Studio Code, so click on the "Open Visual Studio Code" button.

As I mentioned above, you will need two launch tasks, so let's create the client-side one. Head to `launch.json` and add a new "Chrome: Launch" task. Then, you will only need to make one change:

*   Change the `url` value to `http://localhost:3000`

Your complete `launch.json` file should look something like this:

```json
{
    "configurations": [
        {
            "name": "Launch Chrome",
            "request": "launch",
            "type": "pwa-chrome",
            "url": "http://localhost:3000",
            "webRoot": "${workspaceFolder}"
        },
        {
            "type": "pwa-node",
            "request": "launch",
            "name": "Next: Node",
            "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/next"
        }
    ]
}
``` 

And that's it! Now, open the `/pages/index.tsx` file and add a breakpoint on line 9. You can now launch the Launch Chrome task from the debug panel. The Launch Chrome task should open a new Chrome window on the home page. Start typing into the input on the screen and you will hit the breakpoint in the `index.tsx` file. Now you have the ability to inspect the client-side properties, like the `repo` variable. Click continue and type another letter. You will hit the breakpoint every time you type something in the input. Hover on the `repo` variable to see the value changing. You're now debugging the client-side code!

## Conclusion

Now you know how to debug both sides in a Next.JS app. The server side code is node, so you need a Node debug task for it. The client side is Chrome, so you need a Chrome debug task for it.

Also, debugging is a vital process in software engineering, so use it everywhere you can! Don't use only `console.log` for debugging.