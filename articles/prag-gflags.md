# Pragmatism and gflags

My first exposure to Google's `gflags` (C++) library happened a few months
ago, a couple weeks after starting my current job. I was working on a tool that
captured core dumps, parsed the stack traces into a friendlier format,
and uploaded them to a database.

As soon as I started going through the code, I noticed these strange
`DEFINE_{string,integer,bool}` macros in a couple of files. My first
reaction was think "What the hell is going on here? Global variables all around? But
that's so wrong!". Despite the itch in back of
my mind saying that was terrible, I got in, did the work I need to do and didn't worry
about the global variables anymore.

So, for anyone unfamiliar with the library, it allows you to define flags (i.e.,
command line options you pass to the program) exactly where you need them.

Fast forward a couple of months and I became more familiar with the job, our code,
and the patterns generally used. (`gflags` is pretty much ubiquitous around here).

And then today I had to make a change to another project. This one is written in Python. It
publishes data to a data set whose name is hard coded in one of the Python files.
I needed to make this data set's name a command line parameter, in order to run a new instance
of the program; both instances must not publish to the same data set.

As soon as I realized I'd have to make quite a few changes to get the parameter where I needed,
I caught myself wishing I could just use `gflags` and be done with it.

Funny how things change, right? I think there's a message here.

I think Google achieved something great with this little library: it is both very simple to use and
very pragmatic. It gets the job done. Most of the time, when writing a service, you just care
about parsing the parameters you specify and having them available when needed. You don't need
something super fancy for that. You just need to get it done.