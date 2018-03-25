`25/03/2018`

I've had my eys on Go, the programming language, for quite a while. I had a couple of false starts with it a few years ago. For some reason, it just didn't click for me.

Strangely enough, I started listening about it more and more at work. A lot of teams are migrating from Python to Go now.

This got me intrigued, so I started digging through the Go documentation, reading internal code as well as some Go packages' sources. I was impressed. The language quite simple, but very pragmatic. It offers you just enought to get things done without much fuss. And, oh my, channels! They are just a joy to work with. I come from a Python programming background; working with `multiprocessing.Queue` is not even close to being as convenient (and pleasant) to work with as Go channels are.

I also read through Rob Pike's [Newsqueak: A language for communicating with mice](https://swtch.com/~rsc/thread/newsqueak.pdf) paper. You can definitely see the seeds from which Go sprung there. (I absolutely recommend reading the paper if you're interested in Go – it's very readable and quite short).

In my team, we have a data processing pipeline written in Haskell. For various reasons, this turned out to be a bad idea and constantly causes us pain when we need to change it. Seeing the trend towards Go in the company, and the apparent good (though not official) internal support for it, I decided to give it a shot and rewrite the program in Go over a weekend.

I had never written a significant program in Go before, only a handful of small programs to test a few ideas. I sat down, opened [Effective Go](https://golang.org/doc/effective_go.html), the [packages page](https://golang.org/pkg/), and started cranking out code. Mind you, I already knew how to solve the problem, I've been working on this project for almost 4 months now. It was simply a matter of translating code from one language to another. It took me less than 2 full days of work to go from zero to a fully compatible Go version. Actually, this new version had even additional features that were in the roadmap but not yet implemented in the Haskell version. By no means the Go version isperfect and rid of bugs (they are definitely there), but it was damn easy to go from zero to a fully working solution.

I had a blast working with Go, even though I (at first) missed some things not provided by the language: For example, Go does not have a default implementation for _sets_ (this actually makes sense, since there's no generics), which I needed in a part of the application. A little thinking and I figured I could just use a `map` for my problem, which actually turned out to be better. Even though it may not be obvious at first, the language definitely arms you with the tools needed to build anything you might need. Sometimes you just need to shift your way of thinking a bit.

Later on, I showed this implementation to a colleague (who isexperienced in Go) and he quite liked it. He was actually surprised that my code as pretty good for someone who had never written Go seriously before. I attribute this to the fact that the language has a very shallow learning curve (thanks to its simplicity) and the great documentation, as well as the excellent posts in the Go blog (which I also reference while coding).

We are now reviewing the code on our free time, to use it as a replacement for the Haskell code. I'm looking forward to working Go in other projects.