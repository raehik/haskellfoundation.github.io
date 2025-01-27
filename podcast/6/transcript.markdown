_Wouter Swierstra_: So welcome to the Haskell Interlude. I'm Wouter Swierstra and
my co-host today is Andres Löh ...

_Andres Löh_: Hello.

_WS_: ... and I'm very happy to have a friend and colleague on the show today,
Graham Hutton, who many of you will know for his work on Haskell both in
research and teaching Haskell, and in particular his Haskell book. So Graham
will tell us a little bit about how his book came about and give us advice for
how to write a book ourselves, but also look back on his experience using
Haskell and teaching Haskell in the last thirty years, and tell us a little bit
about how bad the compile times were for the very first versions of GHC.

So, welcome Graham, and can you tell me a little bit about yourself?

_Graham Hutton_: Yeah, thanks Wouter and thanks Andres for having me on the
podcast. Very very pleased to be here. So I'm Graham Hutton. I'm a professor
at the university of Nottingham and I do research and teaching on functional
programming, mainly Haskell type stuff. So I'm basically getting paid to have
fun. So don't tell my boss but I'd probably do my job for nothing. I'm doing
kind of Haskell stuff all day every day and it's kind of ... for me, it's a
kind of dream job.

_WS_: Great. So welcome. Um, can you maybe start by telling us a little bit about
how you got into Haskell, because you've been very active in the community for
a long time now.

_GH_: Yeah, so this is quite a long story. So it starts about thirty years ago.
So I was a PhD student in Glasgow, started out in 1989, went up to 1992, and
this was a fantastic place to be a PhD student. I only realized years later
that I was very fortunate to be actually in one of the best groups in the world
and doing Haskell stuff. So in Glasgow at the time we had Simon Peyton Jones,
we had Phil Wadler, we had John Hughes, Mary Sheeran, John Launchbury and many
others. And it was just a fantastic environment to be a PhD student, and it
was also just as Haskell was being developed, and so I can remember when Simon
produced one of the very first Haskell compilers, and it was extremely slow.  I
remember at the time you could type in like a ten line Haskell program, and it
took like five or ten minutes to compile, and everyone's delighted by this, but
of course it was completely impractical. But over time the compiler became much
faster. And this was also at the time when Phil Wadler and others were doing
the kind of the very innovative things in Haskell, so Phil was working on
monads at the time. And I remember all the PhD students didn't understand what
a monad was. We used to go to the pub and secretly say "do you understand what
a monad is?" and everyone said "no, not really". And it's the same today. I
mean people still say "do you understand what a monad is?" It's one of the
classic kind of Haskell questions. And they were also developing type classes
at the same time, and that was that was another ... I got monads quite easily.
But I just didn't get type classes, and when I finally understood them, it's
like with many things in Haskell, you think there's actually nothing much here
to understand. It's actually very very simple. So. And another thing I'd
reflect on in my kind of early days with Haskell is, I mean, the group
community in Glasgow was absolutely amazing. I mean, we had weekly talks, and
we had visitors from all over the world and, crucially, we all went to the pub
on Friday and this is, I mean both of you have visited me in Nottingham a few
times, I mean, Wouter has been a PhD student at Nottingham. I mean we've tried
to have the same kind of culture in our group here. We have tried to have a
very friendly culture, very collegiate culture. Weekly talks, lots of visitors.
And when I reflect back on my PhD time in Glasgow, it was just an amazing time,
and I feel very lucky to being part of the kind of early days of Haskell.

_WS_: So without getting into too much of the technical details, can you say
something about what your PhD was on?

_GH_: Um, it was about relational programming, not functional programming. So
Mary Sheeran was my supervisor, and she was very interested in kind of high-level
approaches to designing hardware, and she had a relational language called Ruby
for designing hardware, and I worked on various theoretical parts of that
and also did an implementation of it, but I was always secretly jealous of the
the Haskell people, so when I finished my PhD, I swapped over from doing the
hardware stuff to doing Haskell stuff.

_AL_: So what exactly was the relation at the time, like Mary and John and Phil and Simon,
as you mentioned, they were all professors even back then, and they were teaching, and
they were all working together or was it separate groups or ...?

_GH_: Ah, yeah, no, it was one group. I mean there was the functional programming
group. All of these people you just mentioned were in it. Um, and all doing
different things. I mean, Simon was working on the compiler. Phil and John
Hughes were more on the theoretical side. Mary was doing the kind of hardware
design stuff, but it was all very much part of the same group.

_AL_: And who were other PhD students there at the same time with you?

_GH_: Ah, so this was also a great time to be there. So Andy Gill was a PhD
student there. Stephen Blott who was one of the people who together with Phil
Wadler invented type classes. Um, I struggle to remember, this is one of the
things I was thinking when you said you might ask me about some early history
in Glasgow, it's thirty years ago, the memory fades a bit. So yeah, it's ...
Andy Gill, and Kevin Hammond was there as well. I can't remember whether Kevin
was a PhD student or not, but he was one of the early Haskell implementors as
well.

_WS_: Was Simon Marlow around at the time or was he a bit later?

_GH_: I was ... I am not sure where Simon did his PhD. He may have been in
Glasgow, he may have not been in Glasgow, but yeah, the memory fades. I mean,
Bryan O'Sullivan is someone who was certainly in Glasgow for a while. But I
think he just arrived just as I was leaving, so that I didn't get to meet Bryan
until much later, but all the Haskell people came through Glasgow at one time
or the other.

_AL_: Was it clear to you at the time that ... probably not, I would imagine, but
nevertheless ... that this would be something that you would still be doing
thirty years later or that this would be something that anyone in the world
would still be doing thirty years later?

_GH_: Ah, no, not at all. I mean, I had no career plan or no kind of foresight at
this time at all. I mean I didn't actually intend to do a PhD at all. I had a,
when I finished my undergraduate degree in Glasgow, I got offered a very nice
job in industry, and it was Mary Sheeran who convinced me to do a PhD. She said
"oh, we've got some money, you can work on this hardware design stuff", and I
just went for it, and I worked on that and then after my PhD, I moved over to
the Haskell side and I didn't really think about where this was going or
whether there was a future in Haskell. I just did something that I enjoyed and
it turned into a whole career.

_WS_: So after your PhD, I think the Ruby stuff was all fairly relational,
calculational and categorical, and so there was this this beginning, I think,
of of a theme, I think, that you continued throughout your career, which is in
program calculation in Haskell. I think this started off maybe in collaboration
with Erik Meijer, and the whole Bird-Meertens Squiggol school of thought in the
kind of early, mid nineties, I guess ...

_GH_: Yeah.

_WS_: So how did you go from from hardware stuff to Haskell stuff? Was that a
natural step or did that take some ...

_GH_: No, it was ah it was a very natural step because as you say most of my work
is about program calculation and so it's kind of applying simple algebraic or
equational reasoning to improve the performance or improve some aspect of your
program. And that's what I was doing with the relational stuff, with hardware
design with Ruby. But the reason I gave up with relations is there was too many
things that were true. There was just too many laws to remember. If you were
embedded in this stuff 24 hours a day you could do it, but outsiders found it
very hard to to understand what was going on, and that was the main reason
actually I moved over to the Haskell side, because the equational reasoning in
Haskell is much much simpler and you don't need to be kind of living and
breathing the laws all the time to be able to do the stuff and to read the
papers. Whereas if you're trying to read papers about relational reasoning, you
really need to be a specialist. Anybody with some basic functional programming
training can read a paper about kind of program calculation in the Haskell
setting. And that's what attracted me. I mean, something that's been very
important to me throughout my career is simplicity, so trying to do things kind
of that are clear, concise and correct, and trying to do them as simple as
possible and using the simplest tools for the job. And for me, many times or or
most times or kind of all the time, Haskell is the right tool for the kind of
things that I want to do, and I want to write papers that are accessible to a
broad audience including undergraduate students, so I have to try and use
things which is accessible to them.

_WS_: So I think that kind of follows nicely onto a next question which is how
you use Haskell. Because I know from experience that you you mostly try to
stick to Haskell 98, and I think you're a big proponent of the Simple Haskell
movement, without doing a gazillion, you know, starting every file with 98 type
extensions. So how do you look back at how the language has changed over the
last you know, well, 30 years?

_GH_: Yeah that's really interesting. So I'm a big fan of simple Haskell. I
didn't really know about the Simple Haskell initiative until I came across a
blog post about it and then I thought "that's me, that's that's what I do I
really". For me, kind of less is more with Haskell. I'm very much into the kind
of holy trinity of functional programming, I think this is Richard Bird's term.
It's kind of recursive types, recursive functions and inductive proofs, and you
can do so much with that. So of course Haskell's developed hugely over the last
30 years and there's lots and lots of new features. But I do I do think as a
community we need to be a bit careful with these features. Remember I saw at
the Haskell eXchange in London five or so years ago, Don Stewart gave a very
nice talk about how they were using Haskell in his job. I think that he was at
Standard Chartered at the time. And he was basically saying they used Simple
Haskell. And the reason for this is if you use the fancy features, maybe you
can be more abstract in writing your programs, but then it's difficult for
people to read your programs, including yourself. I mean, I've used a few weird
extensions in my time. When I come back and look at my code which uses ten
different extensions, I can't understand my own code. So how is anybody else
supposed to understand it? And it's the same with modifying code as well. I
mean, if you use lots of fancy features, maybe it makes your code very concise,
but it's hard for you and others to modify it. So I think as a community, I
mean it's right that the Haskell community pushes on the kind of bleeding edge
of language design and new features particularly with the type system, but we
need to be careful and and use the right tools for the job and don't kind of
abstract for abstracting's sake.

_AL_: It's an interesting point that you make about abstraction making
potentially code harder to read. I mean, that is certainly the case. It's
interesting though that you seem to attach this to language extensions, because
many of these abstraction layers are already possible with Simple Haskell. So
where exactly would you draw the boundary? I mean, if you if you look at monads
and appplicative functors, but also optics like lenses and so on and so forth,
they are all possible to express with simple data types and simple functions if
you want. So you can build your tower of abstraction quite high already while
sticking literally to Simple Haskell every step along the way. So what exactly
is the sort of the threshold for you where it stops being simple?

_GH_: Ah, so I've only got a small brain, Andres, so this has been an advantage
throughout my career. I mean, I see people like Simon Peyton Jones and John
Hughes and Phil Wadler, and these people have brains the size of the planet
and, yeah, I don't have a brain like that. So for me, I need to be able to
understand things and explain things to others. So, but you're quite right. I
mean, maybe the most abstract things that people do with Haskell, you can do
with basic old-style Haskell 98 or Haskell 2000 or something like that. You
don't need the fancy extensions. But I do have a bit of a concern that the
community is kind of too obsessed with abstracting things all the time and it's
like, if you, if someone writes one piece of code and notices a pattern, they
abstract it out, and that's great and it's a lot of fun to do that. But I think
as a community, we do need to be quite careful not to abstract everything for
abstraction's sake and kind of write clear concise correct code. And from time
to time, there may be a nice abstraction which is very useful like moads or
applicatives. But yeah, as a community I think we do need to be very careful,
because it's quite off-putting to outsiders, I mean, no matter what happens
with Haskell, what kind of fancy features go into it, I will always be a
Haskell person and will always love to teach it. But there's a whole community
of kind of people who are one level below being active Haskell researchers, who
maybe like to teach and use Haskell, and it's quite difficult for them to keep
up with the changes. And I do worry that if the community pushes the changes
too much, you might actually end up alienating the vast numbers of extra people
who are really multiplying the impact of Haskell in education and in industry.

_WS_: So I agree with your point to some extent, but at the same time, sometimes
some of these extensions really make your life easier or can really help kind
of keep your code clean, right?

_GH_: Yes.

_WS_: So GADTs are a good example where if you want to write an interpreter for
some embedded language or something, right, where suddenly instead of having to
worry about all of these things which could never happen, the code really
becomes exactly what you want to write in a way. So there's certainly this
tradeoff between powerful extensions versus, you know, simplicity in a way,
right? Sometimes these extensions can help you keep your code clean. So can you
reflect on that?

_GH_: Yeah, so, I mean, that's a good point. I mean, one thing I'm very conscious
of is I'm not a real Haskell developer like Andres for example, so in my
day-to-day research work, I don't have need to use things like lenses and
optics, for example. I just, that's not the kind of thing that is helpful to
me. But i'm fully aware that the people who are who are writing hundred
thousand lines, million lines Haskell programs in industry, they need that
stuff to actually, to get their work done. So I think, well, Andres is shaking
his head, maybe you don't need this stuff to get your work done, but my
impression is that some people need some of these ah more fancy things to get
their work done.

_WS_: This is something that I've encountered as well, I mean talking to PhD
students who were kind of around in Nottingham at the time and then who went to
work for a big bank or some other company. They suddenly said, well we do these
records in Haskell and it all seems very simple, but then suddenly when it
comes to the real world and you want to model something complicated, you
suddenly need, you know, records nested five levels deep and then you want to
change one thing and then all of a sudden you really need some form of lenses.
But even then, I suppose, you have this tradeoff between do you want to use the
most general, most powerful thing possible or do you just want a functional
getter and setter and have some Template Haskell to automate that for you.

_GH_: Yeah, no exactly, I mean, so something I'm very conscious of, I mean, when
you read the Haskell reddit or the Haskell mailing list, I mean there's, I mean
that people talk about this pyramid of people. I mean, there's people at the
top like Simon Peyton Jones and Edward Kmett who understand absolutely
everything and then ... What we need to be careful with as a community is that
I mean those those guys are are the world's best and they understand everything
and yeah, we don't all need to do what people like Edward do, for example, like
I mean he's an amazing person and he comes up with amazing abstractions, but
for kind of Joe programmer in the street or Joe researcher like me, probably I
can get away with simpler things, and I just think as a community, we need to
be a little bit careful not to push kind of going too abstract. I mean, I agree
with your point, right, or maybe it's right to abstract just as much as you
need, but not more than that. But it's very tempting to do that. I mean, I know
as a researcher, and I imagine as a developer too, it's very tempting if you
see a pattern to make it super abstract or use the most general version of a
library, but in terms of the perception of the community and growing the
community, I do think we need to be very very careful to not use abstraction
for abstraction's sake.

_WS_: Yeah, so I think the Foldable-Traversable-Proposal is one good example
there, right? I can understand why people don't want to kind of implement a
length function over and over again and call it tree length or tree null, or
kind of prefix things, or have to deal with, you know, module imports hiding
certain definitions to avoid conflict and all of that. At the same time, it is
something which can confuse people, right? Because you can sometimes get
unexpected behaviour or code, which if you still think of null only working for
lists, it suddenly type checks where it should have, you were expecting a type
error in some in some sense.

_GH_: Yah, so I mean, I was one of the, I mean the Foldable-Traversible thing is
something which I was not very keen on when it was being proposed and voted on.
But actually, I mean, since, I was worried it would it would have a negative
impact on how I teach Haskell, for example, but actually it didn't. If you
design your course carefully and you design your examples carefully, I mean,
students just don't trip up. I mean, once in a while, one of the very good
students trips up on something and gets a strange error message, but that's
okay, because then you can have a conversation with them about it. But, yeah, I
did worry about the Foldable-Traversible stuff, but in practice it's had
essentially zero impact on how I teach Haskell, which is good, because I did
worry about that one.

_WS_: Yeah.

_AL_: I've had similar worries and I've made similar experiences, so it is mildly
annoying, I would say, but it is not quite as bad as originally expected.

_GH_: Ah, no.

_AL_: Also, I mean, I	think the most controversial instances are probably the
tuple, like the pair instance ...

_WS_: Yeah.

_AL_: ... and the Either instance, ...

_GH_: Yes.

_AL_: ... but in a way the precedent has been set much earlier, right? I mean, so
there has been a Functor instance for these for a long long long time, like
almost from the very beginning, and that one is perhaps less confusing, because
you use fmap less often than, I don't know, length or something like that, but
it is still, I mean, it suffers from the same conceptual problem, right? I mean
you're not expecting that you're, if you're calling fmap on a pair and you you
come in with no advance knowledge about how the Haskell type system and kind
system works, you're not expecting that it affects the second component but not
the first.

_GH_: Yeah, I mean, I've had over the last number of years, I mean, I've had,
maybe two or three students stumbled over that by accident and that was fine,
because then we had a conversation about things and those were usually the very
very bright students and I pointed them to a few bits and pieces, and that was
just fine. But yeah I agree, I mean the tuple instance for these things is
bizarre, even though there's a rationale behind it.

_WS_: So you haven't just used Haskell, I mean, and some of your papers do use
systems like Agda and Coq to ... in your work. So is that something that you're
keen to pick up more on, or is, was Haskell not good enough?

_GH_: So it was mainly for ... So most of my papers are about program calculation
and program reasoning. And I tend to do that on pen and paper. I mean, what I
like to do is find, try and find really really elegant, clear, concise, correct
proofs of things. And I do that on my whiteboard, That's my happy place,
standing at the whiteboard with a pen. But also you want higher confidence that
these things are actually right. I mean, some of the things I do with
compilers, it's there's quite a lot of moving parts involved, you want to make
sure you've got things right. So typically what I do with my papers now is, I
have a formal verification using a proof assistant like Agda or Coq. And that's
typically my collaborators that do that kind of stuff. It's usually my PhD
students, I mean, you've been a PhD student yourself, Wouter, I mean learning
things like Agda and Coq is a great thing for a PhD student to do, because it
makes what they're doing more concrete, they can implement things and it's good
for me, because it means that when people are looking at my papers, they can
have high confidence or absolute confidence that things are right, because the
pen and paper proofs have been checked in the theorem prover. But for me the
pen and paper proofs are still what I want to do. I mean, there's a lot of
mechanical overhead and a lot of boilerplate still currently involved with
doing things in a proof assistant, and you need more experience to do that kind
of thing. So I still do my stuff pen and paper and try to fit my papers on a
whiteboard. When I've got a whiteboard full of squiggly symbols, or two big
whiteboards, then that's my paper. But I can fit it onto two whiteboards and
then I hand it over to my PhD student and say, please formalise this in Coq or
Agda, and then they tell me where I've made all the mistakes.

_WS_:	So what would these systems need, or what kind of system would you need in
order to kind of turn pen and paper proofs into formal, formalized type theory
or whatever?

_GH_: But that's, that's a hard question, Wouter. I think Agda is getting pretty
close. I mean, you can do the kind of equational reasoning which I do, you can
mechanise now in Agda with some of the reasoning libraries, fairly closely to
what you would do on pen and paper. I mean, sometimes you need to do some extra
steps to keep the termination checker happy, for example, but it's actually
getting pretty close. So maybe I should actually learn Agda one day.

_WS_: That can never hurt, I guess. So I think one thing where most people will
know you from is actually your Haskell book. So can you tell us a little bit
about how that came about and how that started?

_GH_: Yeah, sure. So this was twenty-odd years ago. So about 2001. I'd been a
lecturer in Nottingham for about five or six years, and I was lucky enough to
be teaching the Intro Haskell course, and I absolutely loved it. I like
explaining things. I mean, a lot of my papers are kind of tutorial explanatory
in style, and I thought well actually, I'd like to turn my experience of kind
of learning and teaching Haskell into a textbook. And also there was a gap in
the market at this time there was very few Haskell textbooks about, I mean, the
Bird and Wadler textbook, which I still think is the best book ever written
about programming had been around for quite a long time, so there was a gap in
the market. So I spoke to my department and spoke to the university and they
gave me a sabbatical, so I think I had a half year sabbatical ...

_WS_: Mmm.

_GH_: ... in 2001, and I wrote the first half, I just kind of sat at my machine
at home and did nothing else. I just wrote the first half of the book and then
it stalled. And then it took me the the next five years to write the second
half of the book, and I was getting constantly hassled by my head of
department. Why is this book not finished? And it just took forever. But it
eventually came out in about 2007. Then I did the second edition that came out
in 2016, and I learned from the first one, if you write a book just write the
damn thing, don't write half of it and then kind of spend your summers over the
next five or six years. Just sit down, chain yourself to a machine and just do
it. So yeah, I did the the second edition in one year straight through, and
that's, various people ask me for advice about writing books and I've only
written two books, I don't really have much experience with this, but my best
advice is, just finish the thing. So I have a number of colleagues, some of
which you know, well all of which you know probably, all of which I won't
mention, who have half-finished books. The field is littered with half-finished
books and my best advice to anybody is, if you're going to write a book, finish
it. Same with a PhD. That's the most important PhD advice: finish it.

_WS_: So I think ah, that was my experience as well. We wrote this book on
functional programming in Swift, and there what what helped was that I ...
well, two things actually, one is I had collaborators who were kind of very
disciplined and kept me going, and the other was that it was time-boxed, we
said we're going to spend this, I mean, I can spend a summer on this and then
we'll see how far we get and then that's the book, regardless of how far we
got.

_GH_: I think that's a very good approach. It's the same with papers, that's why
deadlines with papers are good, because it forces you just to finish the thing,
and it never going to be perfect, I mean it needs to be good, but it doesn't
need to be perfect, and you can go on for years with these kind of things.

_WS_: Yeah, or find a good technical editor, or a collaborator, someone who will
chase you up and tell you that you need to get your act together.

_GH_: Yeah.

_AL_: So I think the book was rather successful, right? I mean that's at least my
impression from the outside, and probably that's also one of the reasons why
you went back and did a second edition, because you felt it is successful, but
it has dated a bit and you want to revise it. But given that you are the author
of a successful book and you managed to pull this off twice now, why haven't
you been writing more books?

_GH_: It takes a lot of time. That's the main thing, but I do have the burning
itch to write another book. I mean, my publisher Cabridge, they said, oh, what
about a third edition of the book? And I would like to do a third edition, but
Haskell hasn't changed sufficiently much in the last five years. So my my kind
of thought at the moment is to to wait until dependent types, if they ever do
come into Haskell, and then that's probably the time to to do a third edition.
But I have been thinking for many years about writing a book on semantics. I
mean, many of my papers are about kind of semantic ideas, trying to explain
them simply, trying to do things like compiler correctness in a very simple
way. So I do have an idea at some point in the next few years to write a very
simple semantics book, which is based on kind of very simple languages and very
simple principles. And I do think there's a gap in the market for that one. I
mean, when I was a PhD student, and I think it's still the same today, if you
want to learn about semantics, I mean, it's a pretty tough uphill battle unless
you've got a maths degree. And I mean most, there's some amazing books out
there about semantics, but they're pretty hard going for people who don't have
a mathematics background, so I would like to write a kind of more popularist
semantics book.

_AL_: Certainly sounds interesting. I would immediately read it and there is,
yeah, I think there is a gap in the market in that place. Has the presence of
the Haskell book, has that kind of changed your status with the students, is it
like ...

_GH_: Yeah, it's a bit funny, I mean you get, I do enjoy it. Once in a while they
ask for the book to be autographed and it doesn't matter how many times that
happened, I still enjoy that kind of stuff.

_GH_: And they know. I mean it's, every year at the start of my Haskell course, I
ask who has done some Haskell, and when twenty years ago it was very few hands,
these days, I mean, there's a lot of hands go up. I mean, in England now and in
the UK, in the school curriculum functional programming is there, because Simon
Peyton Jones redid the computer science curriculum for schools. So there's
functional programming there. So many of them come with a bit of Haskell. And
yeah, when they come to Nottingham, I mean, quite a few of the students are
already aware that and someone in Nottingham wrote one of the books about
Haskell. And that can be a factor in them choosing, I mean, one of the unique
selling points we have in Nottingham is we teach an awful lot of functional
programming. We've been doing this for 25+ years. We have a kind of significant
group of people doing it. Functional programming now is throughout the entire
degree. It's one of the core things that people learn, so it is actually one of
the selling points when we advertise ourselves toprospective undergraduates, we
say, if you want to do kind of Haskell stuff, then Nottingham is one of the
places to do that.

_AL_: So you said, just to recap a little bit further, so originally we were
talking about your PhD at Glasgow and then you said you've been a lecturer at
Nottingham for a couple of years. Did you immediately transition from Glasgow
to Nottingham and then stay there ever since?

_GH_: No, so when I finished my PhD, John Hughes and Mary Sheeran moved to
Gothenburg in Sweden, and they offered me a postdoctoral position there. So I
went to Sweden for, I think it was two years. I actually had a four-year
position, but halfway through, Erik Meijer, who is one of my longest-term
friends, and Erik was in Utrecht at the time, and he offered me a position in
Utrecht, and I love working with Erik. We wrote some papers on parsing 25, 30
years ago which I really enjoyed. I couldn't miss the chance to go and work
with Erik, so I went and worked with Erik in Utrecht for a year. And then the
job in Nottingham came up and I applied for that, and I've been here ever
since. Absolutely love it. I mean, I can't imagine working anywhere else.

_AL_: You've never ever been tempted by industry in any way?

_GH_: Ah, a little bit. I mean, I've had one or two offers, and some very very
good offers.  Um, my wife says, why am I still an academic when industry would
pay so much more, but it's really the freedom which I enjoy. I mean, I get up
every day and I do whatever I want. And that's an immense privilege, really,
and that's worth a lot to me, I mean, I'm getting older now, I mean, I've still
got many years to go, but at some point I may think about maybe getting a
part-time, twenty percent, position in industry or something like that. But at
the moment I'm not tempted by the industry.

_WS_: Okay. So another thing that you've been very active in over the last few
years, I guess, especially important, is the video-phile work and the videos
popularising computer science that you've released on YouTube. How did that
come about?

_GH_: Yeah, so it came about by accident like many things do. I mean, my PhD was
an accident, half my career was an accident, I didn't really plan anything, it
just kind of happened. So in Nottingham we have this Computerphile channel on
YouTube, which is actually the largest computer science channel in the world. I
think it's just passed two million subscribers. And they asked me if I was
interested in doing something about functional programming, and now I've done,
I think, ten videos on functional programming for the Computerphile channel,
ranging from a video in functional parsing, done things on monads, and one on
lambda calculus which has got nearly a million views now, which is quite, it's
quite surprising that something as obtuse to regular people as lambda calculus
can get a million views on YouTube. So this is something which I find, I'm
really interested in making these kind of videos. I mean, many of my papers are
expository in nature, trying to make them as simple as possible, and when I
started doing the Computerphile videos, it just really was a new outlet for me
to try and get functional programming ideas out to the wider community, because
Computerphile has a huge huge audience, it got two million viewers. So if you
put, so my ideas out there, I tend to do more technical Computerphile videos,
and that can have some impact. I've also been active in turning my courses into
YouTube videos. So I'm one of those people who never made videos of their
lectures and the students hated me for it always. But my reason was, I wanted
the students to come to my classes, I wanted them to come and engage with the
material and engage with me and that would give them a much better learning
experience. But then, of course, Covid happened and we all had to go to to
video. So finally, I was forced to make videos for my courses and, building on
what I'd learned from Computerphile, I thought I'll try and make some kind of
nice, high quality ones and almost make like mini MOOCs ...

_WS_: Mmm.

_GH_: ... mini massive open online courses, based on my intro course, which I
teach to first-years, and my advanced course, which I teach to second-years.
And it basically took me about four or five months of solid work. I did nothing
else for four or five months other than make these videos, but it's something
now which I'm very proud of, and it's one of these things that as you get older
in your career, I'm very proud of the book and the papers and I'm also now very
proud of these videos, because you put a lot of effort into these and then they
can exist forever, basically, and help to kind of promote functional
programming in the wider community. So yeah, I really really doing the video
work and I plan to do more of it in the future.

_WS_: So how did how did the transition go from you, from teaching live lectures
and telling a room full of students about Haskell, to having to do everything
remote?

_GH_: Ah, so I cheated a bit. I mean, I love doing in-person lectures, as I
really get a buzz out of this, it's like a theater performance, and I treat it
like a theater performance. But what I did with my videos is, I made those in
advance. And I just played them as live to the students, and I streamed them.
So I didn't do live video lectures to the students. I spent ages making these
videos and then I just streamed them as if they were live. And the students
were actually very happy with that. I mean, it's good for the students to see
different models. Some people did live lectures, some people did pre-recorded
lectures, they said watch them in your own time. And I pre-recorded them, but
played them as live, and then I could be in the chat.

_WS_: Mmm.

_GH_: So it worked well, but I'm very keen ... I will be teaching my two courses
again next year, and I'm very keen to get back into the classroom with big
groups of students and and do the show as it were.

_WS_: Yeah, I can imagine. I think a lot of university staff feel similarly.

_GH_: I do wonder whether anyone will actually show up to the classes though,
given that everything's on YouTube.

_WS_: Yeah.

_GH_: But that's something I'll deal with later on.

_WS_: Well, there's some things which I find really hard, right, is recreating
some of the interaction or being able to write something out on the whiteboard
and being able to switch from Powerpoint to whiteboard to answering questions,
and all of that I think is is quite hard to recreate if, you know, if you have
a well-edited video, is is is the spontaneity of that, I think.

_GH_: Yeah, so I was conscious of that. So I keep quite careful notes on my
teaching. So I kind of storyboard my lectures, and after each lecture I update
my storyboard for what worked well, what didn't work well, and where to put the
interaction in. So I actually did build in, but it obviously wasn't properly
interactive stuff in my video lectures, but I didn't just use Powerpoint
slides, I used my iPad a lot of the time and kind of showed talked through how
to solve problems, I did quite a bit of live coding as well and just talked
through how to solve the problems, so I was trying to kind of mix it up a
little bit and create the experience of being kind of more interactive and
diverse, even though there was no interaction at all with pre-recorded
lectures.

_AL_: Yeah, so one thing that I noticed, because we, I mean I guess we've all
been doing the same thing, right, we've been switching from live teaching to to
pre-recorded teaching or to at least remote teaching, and one thing that I
noticed is that when you have pre-recorded lectures, you can actually to some
extent spend more time on things that are really fun like answering individual
questions or doing sort of things that are slightly off the main track, because
you have the lectures out of the way, they're there, they're recorded. People
can watch them. And then you can spend the actual interaction time with the
students just on the the questions that the students really have and while I
agree with Wouter that is difficult to recreate some of the typical
interactions, there is certainly in my experience also a positive aspect to
this.

_GH_: Yeah, I would agree with this. But there's something that worried me a
little bit. So I played my videos as if they were live, so I'd stream them to
the class, and then I was in the chat and could answer questions, and there was
zillions of questions in the chat, I mean it was nonstop. And I did worry a
little bit that, I mean, the chat is obviously very interactive and I do worry
that the students were paying more attention to the chat than to the actual
video, because the chat is the live part and it's kind of you don't have the
embarrassment of putting your hand up in a class of four hundred students, I
mean, you just type something in a little box and it's fine. Many students are
happy to do that. So yeah, I personally enjoyed that chat interaction with the
students. There was much more interaction than in a normal lecture, but I did
worry a little bit that they were just focusing on the chat and all the funny
jokes we were making and stuff like that, and not actually watching the
lecture. But then maybe they can watch the lecture again in their own time.
Anyway.

_WS_: Okay, thanks. So, a lot of your research is actually on calculating
compilers. A lot of the recent work that you've done. So can you say something
about why that's a particularly hard or why it's a particularly interesting
problem?

_GH_: So for me, it's a particularly interesting problem. So I've been doing
program calculation my whole life, basically. So the idea is you start off with
a kind of formal specification of what you want and then you transform that
specification into an implementation using equational reasoning or some other
kind of reasoning, and it sounds like magic. But if you set things up in the
right way, it's actually a very elegant way to kind of evolve algorithms. And
compilers was one of the, I think for me compilers was one of those problems
where I think it's a particularly good problem for program calculation, because
you can you can write down the specification for a compiler, what it means to
be correct, quite concisely, and then actually the implementation of compilers,
there's lots of little tricks to get things to work properly or to get things
to be efficient, and how do you get from that high-level specification down to
the low-level implementation. So for me compilers was always a kind of a holy
grail. If you could calculate compilers then that was kind of a decent thing to
be able to do with program calculation. And no one really worked on this. I
mean, there was some early work by Erik Meijer and Mitchell Wand and others,
but I was never really satisfied with it. It always seemed to be either too
complicated or it didn't scale. So many many times in my career I came back to
this problem of calculating compilers, and I failed multiple times. I failed on
it for like 15 or 20 years, and then along came my collaborator Patrick Bahr
from Copenhagen. And we worked together on calculating compilers, and we worked
out a quite simple but very general way to do it and I think now we've got a
little kind of cottage industry of producing papers on compiler calculation.
Done it for stack machines, register machines, dependently typed languages, all
sorts of things. So we've got a nice little paper machine here.

_WS_: Yeah.

_AL_: Okay, so to switch to a slightly different topic. So you've been doing all
sorts of community work as well. Perhaps you can highlight a few things there
and go into a bit of detail on some aspects?

_GH_: Yeah, this is something I also very much enjoy and this is again going
right back to my early days as a PhD student in Glasgow. There was a lot of
community activities, both within the group and kind of nationally and
internationally, which was coming out of that group, and I got a huge amount
out of that. So when I got the opportunity to get involved with these things
myself, it was something I was very very keen to do. So early in my career I
was chair of the Haskell Symposium. Both of you have also been chair of the
Haskell Symposium. It's a really fun thing to do, and with community work as
you know yourselves, if you do a good job and you put the work in, people
notice and then they ask you to do more and more stuff, and this is something
which I've really very much enjoyed. And so for example I organised the ICFP
conference, the International Conference in Functional Programming. I organised
that in Scotland, in Edinburgh, a few years ago, and that was a huge privilege,
and also a huge amount of fun to do something like that. I also had the
opportunity to get involved with the ACM, which is the the main professional
organisation for computing, and there's a part of that called SIGPLAN, which is
the Special Interest Group on Programming LANguages, and I was the the vice
chair of that. Phil Wadler was the chair, and we had tremendous fun just kind
of overseeing all the conferences in the area of programming languages, and
again it's just a way to give things back to the community. I meanm I've got so
much out of the community. It's given me an amazing career. Which ah, it's an
absolute privilege and so I've always wanted to give something back to the
community by going into these kind of roles, these community roles and trying
to make things work. I like making things simple and making things work. And
it's not just in my research and teaching, I like to try and do the same with
organising things. So I've organised many many many research events over the
years. I'm involved with the Midlands Graduate School, which is a training
program for PhD students, it's been going nearly 25 years now. I get a lot out
of these things. So I'm very very happy to be involved with them.

_AL_: Perhaps you could explain briefly what SIGPLAN actually is and what it does
and what it involves being somehow ...

_GH_: So SIGLAN is the special interest group for programming languages. And its
main job is to oversee all the programming languages conferences. So I don't
know exactly how many there are but, ballpark, maybe there's kind of 15 main
programming language conferences. And then there's maybe 30 to 50 kind of
workshops which are bolted onto these, and yeah, SIGPLAN's main task is to
oversee the health of the field via the management of these conferences. So
they're always on the lookout, is there conferences that should be existing
which don't currently exist in the field of programming languages. Is there
conferences which should disappear? Actually this is a bugbear for me:
conferences never seem to disappear. We just get more and more of them. Maybe
some should be coalesced, and there is some discussion about that in SIGPLAN.
Do we really need three or four major international conferences every year in
programming languages? Maybe we just need one? So that's the kind of thing that
they're discussing. One thing I'd say about SIGPLAN: if anyone gets the
opportunity to be involved with it, I would jump at it. To an outsider, if
you're just going to these conferences or going to the workshops, you think,
why do we need an oversight body? What do they actually do? Is this just a
talking shop  That's consuming money or something like that? And when you get
inside it, you find it's a group of really really motivated people, trying to
make the field better by improving these conferences and just making sure
they're going in the right direction. And you learn a tremendous amount about
how the field works, and how different parts of the field work. I went to
object-oriented conferences, for example, which I'd never been to before, and
that was a real education to see that. So if anyone gets a chance to be
involved in any kind of community activities, including SIGPLAN, I would say
definitely jump at it.

_AL_: And how do you get into this? I mean, are you asked or are you, do you have
to like ...

_GH_: You can put yourself forward. Basically, I mean there is a nomination
process every year. You can ask somebody else to nominate you, or you you can
nominate yourself and particularly for ... To be honest, if somebody wants to
be on SIGPLAN, they can probably be on SIGPLAN. There's not a huge queue of
people waiting to get involved with stuff like that. So yeah, it's a great
opportunity.

_AL_: But it's primarily academics, would you say, or are there industry
representatives?

_GH_: There's industry people there, too. They're very careful to have a balance
between ... it's primarily academics, because most of the conferences are
primarily academic, but they do want industry people on the committee as well.
So for example, Satnam Singh, who you both know, who's a big figure in the
functional programming community, he was on the SIGPLAN committee recently and
we, and really enjoyed it.

_AL_: So one other thing that you mentioned in terms of community work that
you've been involved in is the Midlands Graduate School. So can you tell a
little bit more about that ...

_GH_: Sure!

_AL_: ... and was that your idea or were you just in the right place at the right
time or ...?

_GH_: Right place at the right time. There was a few of us involved. So the
Midlands Graduate School in Foundations of Computer Science, to give it its
full title, but it's usually just called the MGS, so this has been running, I
think, 20, 21 years now and it was formed by a little consortium from the
Midlands area in England, so Nottingham, Sheffield, Birmingham and who's the
other one?

_WS_: Leicester.

_GH_: Leicester. Thank you, Wouter. So these four universities, and it was formed
because at the time, 20 years ago, we didn't have enough PhD students ourselves
to put on courses. So we kind of pooled our resources and thought, well we can
teach courses to our own PhD students, and that worked really well, and it grew
over the last 21 years, and now it's I think one of the main training events
for students in theoretical computer science, mainly with a programming
language semantics slant on it. One ff the main training environments for those
kind of students in Europe, but we do have people coming from America and
further afield as well. These days, it gets about a hundred ...

_AL_: It's open to everyone?

_GH_: It's open to absolutely everybody. So we get about one hundred participants
per year now, and the fantastic thing is, about twenty percent are from
industry now. So this never happened. Five years ago, I mean, industry people
were not so interested in learning about kind of the hardcore theoretical
computer science semantics type stuff, but that stuff is relevant to industry,
as people are finding out. So twenty percent coming from industry now to the
Midlands Graduate School is fantastic.

_WS_: So one of the things I'm involved in is this Summer School in Haskell that
we run in Utrecht, and there I usually advise people to read your book, or
parts of your book as a preparation, but one of the kind of lacking bits in
Haskell literature, I have the sense, is where do you go after reading your
book, because I feel like so much knowledge of how to use QuickCheck
effectively, or how to use GADTs and maybe some of the more advanced type-level
features is very implicit. It's spread out over research papers, which may not
be very accessible, because they might do things like design a type system
rather than teach you how to use it effectively. So what advice do you give to,
say, starting PhD students on what to do after they finish reading your book
and they've taken your course, and they want to know more?

_GH_: Ah, so that's a good question. The usual advice is go and get a job at one
of the banks in London, and they will train you up and then you'll learn all
the real stuff that we don't teach you. I mean, the textbook field is changing,
I mean there's a whole bunch of textbooks being written at the moment, which
are focused on actual getting stuff done with Haskell, I mean I won't mention
the titles because I'll get them wrong, but there's more than one being written
by people who have been working at the coalface and in industry for many years
and, yeah, explaining all of the kind of stuff that you need to get actual work
done and I think that's a real gap in the market at the moment. But in terms of
the practical question, when our PhD students finish, we say go and work in one
of the banks and they'll sort you out.

_WS_: Well, there must be ... so what ... maybe the question, I should rephrase
the question. What are the missing chapters from your book, or what's the the
research paper that you would recommend people look at after they've read your
book? And something, some pearl or some library that you wish you'd had to the
space or time to include in your book?

_GH_: That's a tricky question. I've put everything I know in my book, basically, so yeah ...

_WS_: So what about like the bananas and barbed wire stuff, right? There's this,
none of that is in in your book and it's not something you would ...

_GH_: No, I've kind of went off that topic. So, I mean, this is going back to one
of the original things we were talking about, about abstraction. So a lot of my
early work was about recursion operators like folds and unfolds and bananas and
and all of that kind of stuff, and I really enjoyed that stuff, but the papers
become quite tricky for people to read, including myself. When I go back
someday, we were talking about the, but the original bananas paper, Bananas in
Space, which shows how to extend folds to function types, somebody was asking
me about that paper just this week, and I went back and looked at it, and it
took me quite a long time to understand my own paper. So if you're saying,
would I recommend people to read that kind of stuff, I'm not so sure. It's kind
of, I enjoy doing that stuff, but I've moved away a little bit from that that
that kind of stuff now. But it's very elegant stuff using these kind of initial
algebra, final co-algebra fancy things. It's very elegant. But yeah, you divide
your, you slash your audience a lot when you have that kind of stuff.

_WS_: Well, to some degree, yes, but at the same time, some of the difficulty
with reading those papers now is that notation has changed, or Haskell has
changed, or it's ... and especially the Squiggol era is, there was this time
where everyone was inventing their own notation and fancy brackets to ...

_GH_: Yeah, people have moved away from that. I mean, Richard Bird and others had
this squiggoly notation, and they abandoned that as well in the end. And
Richard just uses Haskell notation now when he's doing his calculations, and I
mean he was one of those people who also started off, or also got involved with
the relations and went heavily down that route and very squiggly symbols and
funny, some funny notations, but in the end he came back to the simple Haskell
notation as well. And I also think Richard's a Simple Haskell person.

_WS_: Yeah, definitely, well, especially if you look at his books on ... and
functional pearls. There's not much beyond Haskell 98 there, I guess, yeah.

_GH_: Yeah, I mean just going back to the pearls and about what I would suggest
people to read, I mean, I think functional pearls are a gold mine of kind of
interesting simple things to to look at. So yeah, I always recommend people to
go and look at functional pearls.

_AL_: Okay, so to slowly move towards an end, perhaps ... So, Graham, is there
anything that you would like to do in the next few years or anything that you
would like to see happening in the Haskell community, perhaps, like anything,
any wishes for the future?

_GH_: Okay, so I'll answer that from my personal perspective. So I should have a
good answer to this one, some big problems that I want to work on, but
actually, I don't. I mean, I've always taken a quite freewheeling attitude to
research, and I just find what's interesting at the time. So I don't really
think my grand goal for the next 10 years, or before I retire, is to do such
and such a thing. I just like finding interesting problems, kind of getting
buried in them, trying to find the essence of it, and trying to explain it in a
clean and simple way to to people, basically, so yeah I should hope my boss
doesn't listen to this, the university doesn't listen to this. I don't have a
master plan, I'm just doing what I enjoy every day, and actually that's the
privilege of being an academic. That's why I'm in a university and not an
industry, because I come to work every day and I can just work on whatever I
find interesting.

_WS_: So I think that's my experience with research as well to some degree,
you're fumbling around in the dark, trying to even find the right questions to
ask, and once you you bump your head a few times and then you kind of converge
on something, and then you realize that the the solution is really not ... it
was there all along, right, in a way, but just finding, it's never a direct
line, right? Where you start and say, here's my grand plan, I'm going to do
these three things, and then I'll have the solution, then I can publish seven
papers in the next year ... It's always, I wish I knew more about that, and
then you start kind of looking into something, and then you realize that it's
connected in some to something that you did previously, or that you looked at
before, that you kind of ... and then you fumble around and reinvent things
seven times and then finally things start to click, and you realise, oh
actually, I should have seen straight away that it's all very easy and there's
a nice solution.

_GH_: Yeah, this is how research works. People just fumble around and they find
something, and then once in a while something interesting comes out of it, and
I think it's why the whole funding model is wrong, I mean, the funding model
worldwide is based on larger, longer projects. And that's not the way that
great research gets done. I mean, it's just somebody comes up with an idea and
something happens. And actually, yeah, that's a topic for another day, but the
funding model is is all wrong. They should just ... I'd be happy ... again, I
hope the funding council doesn't listen to this ... I'd be happy with a PhD
student every year and a bit of travel money. That's what I need to do my
research.

_WS_: Yeah.

_GH_: And a whiteboard pen. I don't need millions of pounds. It's nice to once in
a while get larger grants, because you can hire postdoctoral researchers and
things like that. But the research which I admire that other people do doesn't
come out of large projects. It's just people having good ideas and having good
people around them and that's what we should fund.

_AL_: Certainly one of the things that I personally, from my personal
perspective, I mean, see as one of the big differences between academia and
industry, that you have freedom about the questions that you ask, right? I
mean, so that's what you're mentioning, and it's sort of one of the, I think
perhaps one of the things that people often don't realise about research, is
that you're not setting out to answer a particular question. You're trying to
make progress on a particular problem, perhaps, but the question, the precise
question that you're asking is as flexible as the answer in a way, and you can
kind of move both ends until you manage to give a satisfactory answer to a
satisfactory question, and I think that is really quite interesting. It is also
something where I think industry is really different, because you're still
having lots of interesting problems to solve, but very often ... well, there is
a little bit of underspecification, obviously, because nobody knows exactly
what they're setting out to do. But there are actual constraints and you have
to stay within these constraints, and at the same time, the funding model is
certainly something that turns academia unnecessarily much into an
industry-like setting, where you have to make up your mind in advance, or at
least you have to pretend that you do and ...

_GH_: Yeah, I mean, one thing to say, at least in the UK the funding councils are
quite realistic. Once they give you the money, they don't actually mind what
you do with it, as long as you do something, and I think that's really
excellent. I mean, some countries micromanage you once you get the money, but
that's a terrible way to manage science. But yeah, when we get the money, they
just leave us alone and they're happy if we do something with it.

_AL_: So more concretely, perhaps we, I mean we talked a little bit about your
goals on the teaching side. You still want to do more videos. You still want to
write a book perhaps on semantics. On the research side, in your in your main
topic, in this calculating compilers topic, you've been making a lot of
progress also in the last few years, but do you feel like most of that is
actually done now?

_GH_: Yeah, I do. So I think we've done most of what we want to do now. I mean,
there's a question of scaling it up, but that would require funding. I mean,
something I didn't mention is that my research has naturally pivoted about
every five years, and this is now coming to the end of the kind of five year
period of doing compiler calculation. So I don't know what's coming next, but
when I look back through my career, I worked on kind of functional parsing for
a while, kind of recursion operators for a while, exceptions and interrupts for
a while, and yeah, most recently on compiler calculation, so yeah, I actually
don't know what's coming next and it's not something I worry about. I mean,
just one day you wake up and you think, oh, that's an interesting topic to work
on, and suddenly you've written five papers on it and yeah, so it's not
something I worry about. But yeah, probably now is the time to start to, for me
to personally think, what is the next thing to work on, because I think we've
done most of what we wanted to do with the compiler calculation stuff.

_AL_: Do you also let yourself be inspired by your PhD students? I mean, are you
mostly telling them what to do or are you letting them tell you what ...

_GH_: It depends on the student. I mean, some students like a lot of direction
and some students come and tell me, this is what I want to work on, and both is
absolutely fine. But I mean PhD students, I mean people is the best part of the
job. I mean, working with undergraduate students, teaching those, working with
PhD students to help them to kind of develop the research, helping postdocs to
develop, and also helping academics to develop as well. That's quite a large
part of my job now as well, kind of helping people to develop their careers. So
yes, it's the people part which is which is the most fun part really.

_AL_: All right, I think this covers about everything that we wanted to discuss.
Thank you very very much, Graham, for being here and sharing all these
experiences.

_GH_: It was an absolute pleasure. It's always great to talk about functional programming stuff, and then particularly with two of my friends. So thank you very much for the invite.

_AL_: Okay, yeah, thank you. Bye ...
