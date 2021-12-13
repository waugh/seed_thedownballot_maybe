## History

This file is an archive of old struggles that are resolved.

I think we want [ReactDOMServer](https://reactjs.org/docs/react-dom-server.html).
What flavor of JSX translation must we specify to the Typescript compiler
(`tsc`) to make it translate JSX into the notation that ReactDOMServer will
 understand? According to [Anup Shinde](https://www.anupshinde.com/posts/react-typescript-server-render/), the answer is `react`. Specifying it on the command line in either of the obvious ways doesn't seem cut it, so now would seem high time to read about how to set up the config file for `tsc`.
 
So [here](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)
seems to be the root doc for the config and it seems to be saying that
`tsc` will ignore the config file if any inpt files are specified on the
command line. If I want to do some little test
in a scratch directory,
I may need to read about the 
(command-line options)[https://www.typescriptlang.org/docs/handbook/compiler-options.html]
after all.

Hmm, this looks useful:

```
npx tsc --init
```

Started the following as a question for Reddit, then thought to try something
else first.

I am trying to get started with some basics.

I am in a scratch directory under my `npm`-based project and I have a file `foo.tsx` containing only:

```
globalThis.t = {};
globalThis.t[0] = <p>Foo.</p>;
```

So this is a quite simple and basic attempt to lay down some JSX and see what JS it gets compiled into. When I use `tsc` it says I need to specify `--jsx` if I am going to use JSX, which seems fairly reasonable. So I try it and it says I have to choose from about four or five flavors of JSX translation. Based on what I am trying to do with the output and someone's friendly post, I decide on the translational flavor `react`. Fine. So, the obvious way to put that in an argument would be (after eliminating the standard construct that uses the equal sign),

```
npx tsc --jsx react foo.tsx
```

But this still produces error TS2304: Cannot find name 'React'.

How can I use `tsc` to compile my JSX for feeding into
[ReactDOMServer](https://reactjs.org/docs/react-dom-server.html)? Blogger
[Anup Shinde](https://www.anupshinde.com/posts/react-typescript-server-render/)
says that `react` is the correct flavor. Hmm, maybe I have to download React.
Would have to do it soon, anyway. At least, the part of React that provides
ReactDOMServer.

```
npm install react-dom
```

The install went OK, but I still get the same error.

Posting my
[question](https://www.reddit.com/r/typescript/comments/rcs21o/translating_jsx_with_tsc/?)
to Reddit.

