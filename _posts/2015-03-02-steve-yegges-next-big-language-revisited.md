---
layout: post
title: Steve Yegge's Next Big Language Revisited 
---

{{ page.title }}
================

<p class="meta">March 2 2015</p>

Good old Steve Yegge. For several years from time to time you'd get one of his rather opinionated, well-informed, and always entertaining blog posts on topics relevant to anyone doing computer programming. He's been relatively quiet for several years now, but I've always thought one of his most memorable pieces was [The Next Big Language](http://steve-yegge.blogspot.com/2007/02/next-big-language.html).

He wrote that just over seven years ago (wow), and although things have not turned out quite as he expected, and it has never been clear whether he had an existing language in mind or was just spitballing, I think he was close enough on the mark to an existing and still growing dynamo to make this worth revisiting.

I've done work in multiple languages, dabbled from time to time in creating my own as all young people do, and I consider myself a polygot and not much of a fundamentalist about the programming langauge I'll use. While I'd prefer something semantically and syntactically clean and beautiful like [Ioke](https://ioke.org/), my real concerns center around performance, libraries, expressivity, and community. If a language is too lacking in one of those, I'll look somewhere else. And there are languages I refuse to touch because, quite simply, I have standards.

I've used Python as a steady and reliable workhorse for years, and while there are numerous libraries I adore like [Flask](flask.pocoo.org), [Django](www.djangoproject.org), [BeautifulSoup](www.crummy.com/software/BeautifulSoup), [Requests](docs.python-requests.org/en/latest), Python is an inherently conservative language. Someone once explained that to me in terms of Guido Van Rossum and the Dutch drive for conservative practicalism, but as much as I like the sound of that, I have no idea if it is bullshit. What I do know is that with the exception of [PyPy](http://pypy.org) (which has been around for several years and never gained real traction), Python isn't going to get super performant any time soon. It also doesn't currently deal with the modern web (async, concurrency) as cleanly as I'd like. I know there is some work in the area, but it isn't the out-of-the-box solution you'd want to see. There's also the very slow evolution from Python 2 to 3, which isn't really concerning, but does make you pause and wonder if the userbase is always going to be split between the two.

So I've been looking for a language to replace Python. I tried Javascript and found callbacks to be a crime against humanity, found a better concurrency model in Go, but found rather simple things that it couldn't express and Python could. I love Clojure as a Platonic idea, but find the JVM, Maven, and the associated ecosystem a bit heavy for my tastes. Oh, and I know if anyone actually reads this post, they are going to ask "Why not Haskell?", and my response is that Haskell is a great language but it isn't going to become a mainstream language any time soon (or ever). Sorry. That aside, within the last few months, I've seen enough moevement within the Javascript (wait....let me explain) community, and used it enough myself to make me think that Javascript is the closest thing to Yegge's NBL, and not only that, but if you are paying attention, there are signals all over the place that it will be *the* dominant language within five years, and not a horrible one at that.

Now let's get back to Yegge's original article, going through his points one by one.

**NBL does not replace C++**

I'm not going to delve into this really far, but Steve's point here is that while some people don't need garbage collection, most programmers aren't operating under that constraint, and the next big language will have garbage collection, because in the vast majority of cases it makes your life easier. This has been known for decades, so nothing new. Now, if we want to replace C++, there's always [Rust](www.rust-lang.org) and [Nim](http://nim-lang.org)...

**NBL isn't about winning beauty contests**

*If your goal as a language designer is to design a language that meets your own personal sense of aesthetics, then you're an artist, and I salute you. For my part, I'm looking for the middle ground between hard-nosed I-don't-care pragmatism (in which case you go ugly early, use Java or C++, and be done with it) and idealistic better-world optimism. And I think a lot of other people are too.*

He gets into even more detail with this later, but he's absolutely right: Io, Ioke, or whatever other beautiful and conceptually-pure language isn't blowing up any time soon, so a trade-off will have to be made. I think Yegge just invoked Nixon's "Great Silent Majority". You could say Nixon had some issues, but ignoring the politics of that statement at that time, the Great Silent Majority of programmers aren't snobs, idiots, or language partisans, they just want something that will get the job done, and they'll use the best tool they are aware of and comfortable with. 

**Rule #1: C-like syntax**

*C(++)-like syntax is the standard. Your language's popularity will fall off as a direct function of how far you deviate from it.*

*There's plenty of wiggle room in the way you define classes and other OOP constructs, but you'll need to stick fairly closely to the basic control-flow constructs, arithmetic expressions and operators, and the use of curly-braces for delimiting blocks and function bodies.*

*This is because programmers are lame, but hey, it's your target audience. Give the people what they want.* 

Yep, that sounds like Javascript. Javascript has a few ugly parts. I wish semicolons were completely unecessary, ala Ruby. Functions prior to the fat-arrow syntax in ES6 (for those unaware, ECMAScript is the official name of Javascript, 6 is the version) were verbose. However, Javascript firmly falls within the C class of languages syntatically. Anyone who has used C, C++, Java (in other words, the vast majority of programmers), will feel at home. You also avoid the incessant debate over whitepace you find in Python or Coffeescript, and the immediate rejection that some otherwise beautiful languages like Clojure face. 

To make a deeper point about how much this can matter, while I had my own reservations about Clojure and lisp-style syntax (or lack of it), I got over it pretty quickly and appreciate it for its own benefits now. However, that same irregular syntax is part of what keeps me away from it, not because of my own feelings, but because as Yegge says, programmers are lame. A lot of people will reject a language immediately for something as superficial as that. We are human beings, superficial rejection is nothing new. And it is a damn shame, because Clojure is one of the most well-thought and well-designed languages in existence. Rich Hickey is brilliant.

Syntax is one of Javascript's blandest parts, but this semi-weakness is actually a great strength.

**Rule #2: Dynamic typing with optional static types.**

*Adding in optional static types is the ideal solution. It helps with performance, it helps with code reliability and (possibly) readability, it helps IDEs navigate your code, and most importantly, it helps combat the incredible FUD that dynamic languages inspire in people who come from static backgrounds.*

*It should be pretty obvious that dynamic + optional static types is a better approach than static + optional dynamic features. The latter is premature optimization, plain and simple: the root of all evil.*

I think these statements will make users of some static languages go nuts (no pun intended), but the gist is correct. Dynamic languages are really simple and fun to start with because they are so free-flowing. There's much less friction. Javascript takes this to a bit of an extreme with its weak typing, but the simple expressivity it has is very much appreciated. It is a great beginning language (especially with the immediate feedback you can get with the browser), and it is easy to adapt to. If you have some experience with any other modern (and not-so modern) language, you can adjust to it quickly.

What about optional static types? While nothing has been standardized, Microsoft's [Typescript](www.typescriptlang.org) is already very useable, and Facebook's [Flow](http://flowtype.org) accomplishes a similar task as a layer above the language. These features are necessary for large codebases with many contributors (at least many people fervently believe this, right or wrong), and Javascript is being used at such a scale that even if static typing is never standardized, these tools and alternatives will continue to get better and more varied. 

Additionally, they are things you can incrementally work into as a young programmer, which makes them even more useful. They aren't an all-or-nothing thing. Static type systems have to carefully balance expressive power, simplicity, and staying out of the way. Dynamic type systems naturally do that, their problem is settling down. Optional types do that, and it is a bit surprising that this Holy Grail of programming is only really now seeing fruition in a dynamic language.

*As a special sneak preview, its static type system will include a "standard" class system (i.e. the kind you're used to if you do any conventional OOP using C++ or Java or Python or whatever, as opposed to Common Lisp's object system or some other unconventional one.) Not that the standard system is any better, but it's what people want.*

Javascript's prototype system has been used to emulate classes for some time now, but ES6 actually standardizes the syntax. Some people hate it ("Get your Java out of my Javascript!"), but it is what people are used to, and undoubtedly helps with standarization across codebases. Just as importantly, it makes the shift from Ruby, Python, Java, and numerous other OO languages very easy.

**Rule #3: Performance**

*NBL will perform about as well as Java. That means if it's one of the big existing dynamic languages out there, something major is going to have to happen with performance.*

I'm sure I could find some benchmarks online that would speak to this, but I'm hesitant to do so. There's that great Mark Twain line (or at least attributed to him) about "lies, damned lies, and statistics". I do know that just due to time and work on the JVM, as well as Java's static nature, it is very unlikely that Javascript is as fast as or will be as fast as Java any time soon (Self, LuaJIT, and Javascript itself show you can get close). But even that is not necessary. You just need fast enough, and the fact that people have been using Python or Ruby happily speaks to that.

However, why are so many people using Javascript on the serverside right now, anyway? Because they hear that Node and Javascript are fast. Compared to most other dynamic languages, this is objectively true. This stems from one of the great advantages Javascript has over pretty mcuh every other language. Millions of people are depending on it through their browsers, and numerous companies are tyring to reach those same people. They all benefit from it being performant. So you've got Microsoft, Mozilla, Google, Facebook, and several other companies pouring thousands of hours and millions of dollars into making it as fast as possible. Nothing else is getting that kind of support. This isn't relevant to just performance, it is relevant to new features, it is relevant to libraries, tooling, etc. This advantage cannot be overstated, and it is not going anywhere because browsers are so reliant upon the language. We have COBOL code running on mainframes right now. We'll have Javascript running on websites 50 years from now, even if we have long since moved on to something else.

Oh, and what happens if optional typing gets used more than a linter and safety and is actually utilized for performance? Google's [Closure](https://developers.google.com/closure/library) library already can benefit from type annotations. [asm.js](http://asmjs.rg), while not intended as a user-level part of the language, takes this even further. With additional type information, Javascript will only get faster and faster. It might even truly challenge Java.

**Rule #4: Tools**

*So NBL will have great tools. They might not be Java-great on Day One of NBL's reign, but they'll be a lot better than the options available for Perl/Python/Ruby/Tcl and the rest of the popular dynamic languages out there today.*

I'll be honest: I'm the kind of guy who opens vim and codes with minimal tooling (I'm not sure I've ever used a real debugger), so I can't comment on this point with any real knoweldge. However, go back to Rule #3, see what I said about the ongoing work by numerous companies, and apply it here, again. You've already got things like source maps which make compile-to-js languages much easier to debug. You've got great inspectors and debuggers for browsers. npm, while not a tool in Yegge's use of the word, is also one of the better and more integrated package managers. Editors will continue to get better and better with Typescript/Flow integration. It is a simple rule: the more people that use your language, the more tools there will be, the better tools will be. Things which have taken years to build in other languages due to relatively small communities or lack of corporate backing are all over the place in JSland. You have some of the perimer tooling companies working on it already. 

**Rule #5: Kitchen Sink**

*Word on the street is that all languages are evolving towards each other. It's another way of saying they all have feature envy. So NBL is going to have to play along.*

Yegge lists 18 features which he considers "ad-hoc standards". Some features, like destructing, standard OOP with classes, iterators and generators, list comprehensions, namespaces and packages, and keyword and rest parameters have all landed in ES6. In other worse, Javascript has grown up. This should both tell you how lacking JS was in certain features prior to ES6, as well as how quickly the language is improving. He mentions function literals and "non-broken closures", JS has always had fine closures (less imited than Python for exmaple), but the fat-arrow syntax has really, truly made them useable and convenient (and fixed the binding of *this*). He mentions cross-platform GUIs, which counting the browser is perhaps more true for JS than any other language. That is not even considering work on projects like [React Native](www.youtube.com/watch?v=KVZ-P-ZI6W4). First-class parser and AST support certainly exist due to the use of JS as a type of web assembler, and object-literal syntax for arrays and hases is something we all use: JSON.

*Additionally, NBL will have first-class continuations and call/cc. I hear it may even (eventually) have a hygienic macro system, although not in any near-term release.*

His mention of continuations and call/cc are what suggest he had an existing langauge in mind more than anything else. They seemed, even in 2007, as an odd inclusion considering that languages were moving away from them as a feature ("big" languages they were a part of only included Smalltalk, Scheme, and Ruby, and only Ruby was really in the spotlight at the time). JS has a macro system via sweet.js, and compile to langauges could be seen as macro systems in and of themselves assuming they don't choose to include their own.

*Not sure about threads. I tend to think you need them, although of course they can be simulated with call/cc. I've also noticed that languages with poor threading support tend to use multiprocessing, which makes them more scalable across machines, since by the time you've set up IPC, distributing across machines isn't much of an architectural change. But I think threads (or equivalent) are still useful. Hopefully NBL has a story here.*

GvR and the Python community have been advocating IPC for a long time due to the Global Interpreter Lock. Web workers are something similar for Javascript. I personally like Python's [multiprocessing](docs.python.org/2/library/multiprocessing.html) library which gives IPC the same API as interacting with threads, but they obviously aren't directly equivalent and true threading would be useful. JS's asynchronous nature helps in some situations were threading would be used, but it seems inconceivable that a better soltuion wouln't be found over the next few years. Again, the advantages of competition.

**Rule 6: Multi-Platform**

*NBL will run, at a minimum, both standalone and on the JVM. I'm not sure about plans for .NET, but it seems like that will have to happen as well.*

*And there are two other platforms that NBL will run on which, more than anything else, are responsible for its upcoming dominance, but I'd be giving away too much if I told you what they were.*

JS certainly runs standalone on [Node.js](http://nodejs.org) or [io.js](https://iojs.org). It also runs in numerous browsers and because it is designed to be embedded does and will run in numerous areas you wouldn't expect it (and perhaps should not). There's [Rhino](www.mozilla.org/rhino) on JVM, and having done a quick google, there are numerous projects to run JS on .NET, though how far along they are or which one is the dominant project is unclear to me.

*The features I've outlined don't make NBL a great language. I think a truly great language would support Erlang-style concurrency, would have a simpler syntax and a powerful macro system, and would probably have much better support for high-level declarative constructs, e.g. path expressions, structural dispatch (e.g. OCaml's match ... with statement) and query minilanguages. Among other things.*

This is creepily close to [Elixir](http://elixir-lang.org), though it faces the same difficulties of becoming a major language that many others have.

*The features I've outlined are basically the minimal set of requirements for not sucking. At least off the top of my head; I've probably overlooked a few.* 

Okay, so JS doesn't completely suck. Does that fill you with joy as a programmer? I think we all dreamed of spending our next few decades coding in a language that doesn't suck. On the other hand, we all really dodged a bullet there. Brendan Eich threw together JS in a few weeks; things could have been much, much worse.

But...I'll go so far to say that Javascript, against all odds, is actually getting good. ES6 added numerous important features, and most importantly, you can use them *right now* with [Babel](https://babeljs.io), which is a transpiler that both implements the standards and produces relatively clean code with support for source maps so that debugging is simple. I was also very pleased to see that it has support for Flow (again: static type checking), JSX for easy React templating/integration, and even some ES7 features like [await](https://github.com/lukehoban/ecmascript-asyncawait), which pretty much completely removes the language's heritage of callback hell.

Regarding await, look at this code (shamelessly taken from a post by [rzimmerman](news.ycombinator.com/user?id=rzimmerman) on Hacker News):

    app.get('/', (req, res) => {
      try {
        await user = db.get({user: req.user});
        res.send({user: user});
      } catch {
        res.send(400);
      }
    });


I can work with that.

When you put it all together, what does this (the dynamo that is Javascript) give you?

* one of the most performant dynamic languages
* optional static typing/checking
* a massive ecosystem of libraries, easily accessible through npm
* a genuinely exciting way to create UIs with React
* an expressive and relatively good syntax which is both easy to adapt to and won't drive anyone away immediately
* decent and improving tooling
* and to repeat it one more time....a foundation that will exist for years and years and only grow due to its importance to the browser...meaining the best and biggest companies are consantly improving upon the langauge, the ecosystem, and the tooling around it

Hell, even when people aren't using JS itself, this combination of factors makes it *the* compile target, only entrenching it even further. Python and Ruby might have more of a future compiling to and running as Javascript than they would on their own VMs. This certainly is the case for any number of niche and/or hobbyist languages. See [Roy](roy.brianmckenna.org), [Wisp](https://github.com/Gozalla/wisp), or [dozens of others](https://giothub.com/jaskenas/coffeescript/wiki/List-of-languages-that-compile-to-JS) as examples (tools like [Jison](http://jison.org) and [escodegen](https://github.com/estools/escodegen) make JS a great way to learn parsers and compilers, for the record).

Yegge specifically stated that Javascript 2 (a different and dead standard) was not the NBL. However, if he were writing this post today, he might say that Javascript is the NBL. I personally believe that even if it is not currently, reading the tea leaves, it absolutely will be. This excites me a little more than it should. Not only does Javascript not suck, but the idea of semi-standardization on a solid language is something I have wanted for a long time. 

We can drop the **Next** and just call it **The Big Language**.
