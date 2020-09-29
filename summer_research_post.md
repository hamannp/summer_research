# Expanding the OOP/TDD Toolkit: Functional and OO Domain Modelling with Types

## TL;DR This post combines FP and Type Design learning resources from true pros. Check out the links!

## Motivation
Over the years, I've always wanted to expand my OOP/TDD skills with a strongly typed
language, maybe even a Functional one. I love Ruby on Rails, but after more than a decade
I've been itching to get on some more recent bandwagons. Node.js and React written
with Typescript have become very popular. Elixir is gaining popularity with its support
for both FP and OOP paradigms, type specs, and unbeatable OTP/Erlang foundation.
For this reason, I prioritized this particular set of technologies for learning.
However, I ultimately found it useful to remain agnostic about specific languages while
learning concepts. What I really wanted from my learning experience was to accelerate
deeper understanding to gain deeper skills. I mean, what does great type design look
like from a master? Why does functional programming matter? What shape does truly
great FP code have? How does it relate to OOP, and can I mix concepts?

Below is what I've learned so far.

## Strong Typing vs Dynamic Typing
I learned about dynamic typing while apprenticing under a craftsman in an Agile Rails shop.
The big idea that I took away was that iteratively designing systems by example in a
feedback loop with real users delivers quality software with low training and
support costs. You can flexibly make code changes with few regressions since clean,
dynamically typed OOP code is malleable, easily tested, and injects its dependencies.
Those test examples become what you can prove about how the system behaves.
It's an approach that works well with vague requirements and a domain that is yet
to be discovered. Best of all, it delivers more linear complexity for each marginal
feature, making Agile planning and team coordination much easier.

In the past, I've sought a similar explanation on the value of strong typing.
I mostly heard the controversy best summarized as follows by Gary Bernhardt:

> Some people claim that unit tests make type systems unnecessary: "types are just
simple unit tests written for you, and simple unit tests aren't the important ones".

> Other people claim that type systems make unit tests unnecessary:
"dynamic languages only need unit tests because they don't have type systems."

Gary's video is a great place to start on dynamic vs. static typing.
[Ideology - Gary Bernhardt](https://www.destroyallsoftware.com/talks/ideology)

The lights went on for me once Gary explained that good type design can enable
you to use the compiler to statically model and enforce domain invariants and prevent
invalid states. That's inherently a very complimentary approach to defining behaviors
with test examples. What a great idea! He also makes the point that if we had arbitrarily
expressive type systems, then maybe examples wouldn't be necessary. However, a
consistent point made throughout the rest of the links collected here is that good
type design requires overcoming Primitive Obsession. An arbitrarily expressive
type system provides no more value than poorly written or missing test examples
when used naively. In other words, the value of either the static or dynamic type
paradigm is in how it is applied to model the domain.

## The Value of Functional Programming
_**Note:** It took me a little while to understand the constructs common to FP.
I think Miranda syntax would have been a good place to start since it's the original._
[Miranda Syntax](https://www.cs.kent.ac.uk/people/staff/dat/miranda/Overview.html)

The FP explanations that I've heard were mostly about the performance and design
benefits of immutability, especially eliminating race conditions.
Immutability is often called out for enabling more distributed systems as well.
These benefits are valuable, and make a lot of sense.  However, I was shocked to
discover that the original intent for FP was in fact code modularity, composition,
and reuse. In that sense, the original goals of FP were not that different from
OOP. This research paper is worth reading for that perspective.

[Why Functional Programming Matters](https://www.cs.kent.ac.uk/people/staff/dat/miranda/whyfp90.pdf)

This video below is essential for anyone looking to go from a dynamically-typed OOP
background to strong types and FP. Scott's entire website is helpful and well worth the time.
I think his concept of 'Railway Oriented Programming' is very actionable for anyone looking
to 'level up' quickly.  In addition to presenting the 'patterns' common to FP,
Scott brilliantly maps CS jargon to more accessible explanations.

[Functional Design Patterns - Scott Wlaschin](https://www.youtube.com/watch?v=srQt1NAHYC0)

[Scott's Website](https://fsharpforfunandprofit.com/)

The video below from Debasish Ghosh nicely explains the academic concept of defining
'domain algebras' that assemble from lower level algebras into higher level algebras.
He then shows how treating function signatures as data types enables the creation of
implementation-free types that assemble into domain and subdomain modules.
The example that he builds based on securities trading become illuminating when
he plugs in an actual implementation at the very end. It's a fine demonstration of
both composition and managing domain heterogeneity with types. It's well worth hitting
the pause button frequently to more fully absorb each point as he builds on
the concepts. While more academic than Scott Wlaschin's explanations, Debasish's mix of
theory and practice is powerful yet accessible.

[Functional and Algebraic Domain Modeling - Debasish Ghosh - DDD Europe 2018](https://www.youtube.com/watch?v=BskNvfNjU_8)

## Node.js and Typescript Resources
This site is a tremendous learning resource, and potentially, a great reference
architecture for Node.js apps implemented in Typescript. I found it to be a very mature
and complete vision that skillfully incorporates FP concepts into more traditional OOP.
These concepts are at the same time generic and could be implemented in many other
platforms besides Node. In particular, dividing large domains into subdomains and
then communicating between them with events is a well established enterprise pattern.
Bringing that modularity approach to web development is a big win. It would also be
particularly well supported by Elixir/OTP.

[Domain Modelling with Typescript](https://khalilstemmler.com/articles/software-design-architecture/full-stack-software-design/)

## Elixir Learning Resources
These links provide helpful resources for learning Elixir. Elixir relies heavily
on pattern matching. Combined with types, pattern matching becomes an extremely
expressive way for handling different cases. Nonmatches can be caught by a final
clause that returns an error value that can be cleanly matched and handled by the caller.
I was really impressed by the power of pattern matching on a production API that I wrote
at my last company.

[Elixir Koans](https://github.com/elixirkoans/elixir-koans)

[Learn With Me: Elixir](https://inquisitivedeveloper.com/tag/lwm-elixir/)

[Domain Modelling with Sum Types](https://thoughtbot.com/blog/better-domain-modeling-in-elixir-with-sum-types)

[Practice coding](https://exercism.io/tracks/elixir/exercises)

Developers coming from Rails will immediately feel a familiarity with Phoenix, the
Rails inspired Elixir MVC framework. However, it makes some important changes that
have long been sought by many in the Rails community. I like that it gently guides
you to separate web and domain logic, i.e. Hexagonal Architecture. The Ecto component
separates the problematic 'many responsibilities' of AR models. For example, it allows
you to define multiple changesets that can be applied for validation in specific use cases.
[Phoenix](https://www.phoenixframework.org/)

While not specific to Phoenix, this article explains the benefits of
[Hexagonal Architecture](https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749)

Elixir provides an astonishingly elegant abstraction over the venerable
Open Telecom Platform (OTP) Erlang libraries. Out of the box it has strong
capabilities for building distributed, performant, concurrent, fault tolerant
systems. This part of the stack is the real 'secret sauce'.
[OTP](http://blog.plataformatec.com.br/2018/04/elixir-processes-and-this-thing-called-otp/)

## React.js Learning Resources
The two resources below are great hands-on tutorials for React / Redux.  The first
one starts very basic and builds incrementally.  It's particularly good if you're
new to React and FP concepts. If you've used Angular or a similar client-side framework
and you want to get started coding functional concepts, the official Redux tutorial
is a great start.  Either way, the testing section in '30 days of React' is super
valuable.
[30 days of React](https://www.newline.co/fullstack-react/30-days-of-react/)

[Redux Tutorial](https://redux.js.org/tutorials/essentials/part-1-overview-concepts)

The official Redux testing guide is a catalog of patterns and recipes.  They make
an excellent point that pure functions are much easier to test.  You see the modularity
and simplification of the React/Redux state management pattern when you see how
easy it can be to test.
[Official Redux Testing Guide](https://redux.js.org/recipes/writing-tests)

While test examples help ensure the correctness of a program, the link below is a
guide that can help with using Type Design to further that goal. It's very comprehensive
and begs to be applied to a real, complex domain problem.
[React Redux Typescript Guide](https://github.com/piotrwitek/react-redux-typescript-guide)

At the same time that I'm impressed with how easy it is to sync data with a server,
I hear that there are quite a few gotchas in practice.  This link is an authoratative
and comprehensive guide and explanation of the issues and pitfalls.
[Complete Guide to useEffect](https://overreacted.io/a-complete-guide-to-useeffect/)

## Additional Learning Resources
This link is a collection of Haskell articles on good FP coding and testing practices.
[Functional Best Practices](https://williamyaoh.com/posts/2019-11-24-design-and-testing-articles.html)

## Conclusion
From all that I have read and heard, I've come to believe that type design compliments TDD
by giving you more ways to define the domain and ensure the correctness of a program.
FP compliments OOP by giving you another path to code modularity and composition
with less coupling and fewer bugs. There are many additional technical benefits to FP,
some of which can be had by adopting Functional techniques in any language.
Additional FP benefits come from leveraging the architecture of the underlying platform,
particularly with what assumptions it makes about immutability. The real goal is to
provide users with an intuitive and consistent set of experiences from one production
deploy to the next. Expected behaviors that are not defined 'somewhere' will have to
be done manually with costly tech support, bug fixing, and training. The right combination
of business focus, type design, test examples, and consistently applied
architectural patterns will result in systems that better and more profitably serve
people. I feel like technologies such as Node, Typescript, React, and Elixir/Phoenix
have grown in popularity because they help developers accomplish these goals when
applied effectively.
