!SLIDE
# About self()

<strong>^name = "Vasilis Spilka"</strong>

<strong>Backend (mostly) Developer @ Applifting</strong>

Programming in Ruby for 4 years.
Found Elixir over a year ago.

<strong>Skills:</strong>
- Ruby/Rails
- DevOps
- js/Nodejs/++
- Elixir

!SLIDE shout
# Introducing Elixir
<img src="images/elixir-lang-logo.png" alt="" height="200px"/>

## Solving the problems we face

!SLIDE 
# Problems we face today:

- Multicore
- Distributed Systems
- Live systems (Real time systems)
- Increasingly Complex Systems
- Failure, Failure, Failure
- Rapidly approaching deadlines

Can a new language help with these problems??

!SLIDE 
# Erlang/OTP

Language + VM, Created by Ericsson in 1986.

The Erlang VM (Beam) was build to run distributed, fault-tolerant systems.
Software running on the Erlang VM is really fast, and can take advantage of all your system resources,
it also tends to have amazingly high uptime, often more than 99.99999%

!SLIDE 
# OTP
OTP stands for Open Telecom Platform. <br>
Set of modules & standards designed to help you build distributed and fault-tolerant applications based on actor model and supervision trees
through processes with independent state.

!SLIDE quietest smaller-code
# But it looks like this...

    loop(Req, Env, Handler, HandlerState) ->
      receive
        Message ->
          call(Req, Env, Handler, HandlerState, Message)
        end.

    call(Req0, Env, Handler, HandlerState0, Message) ->
      try Handler:info(Message, Req0, HandlerState0) of
        {ok, Req, HandlerState} ->
          loop(Req, Env, Handler, HandlerState);
        {ok, Req, HandlerState, hibernate} ->
          suspend(Req, Env, Handler, HandlerState);
        {stop, Req, HandlerState} ->
          terminate(Req, Env, Handler, HandlerState, stop)
        catch Class:Reason ->
          cowboy_handler:terminate({crash, Class, Reason}, Req0, HandlerState0, Handler),
          erlang:raise(Class, Reason, erlang:get_stacktrace())
        end.

    suspend(Req, Env, Handler, HandlerState) ->
        {suspend, ?MODULE, loop, [Req, Env, Handler, HandlerState]}.
        

!SLIDE
# The Vision by José 

    Platformatec.José
    |> Book.read(:seven_languages_in_a_week)
    |> Book.discover(:Erlang)
    |> Emotions.like(:things_he_saw)
    |> Emotions.miss(:things_he_dident_see)
    |> Work.create(:Elixir)

!SLIDE 
# Elixir!

- <strong>Functional but allows side-effects</strong>
- <strong>Immutable</strong>
- <strong>Dynamic (with typespecs)</strong>
- <strong>Sweet (Ruby-like) syntax</strong>
- <strong>Runs on Erlang VM</strong>

!SLIDE
# Basic Types
- String (often referenced as Binary)
- Integer
- Float
- Boolean
- Atom (Symbol)
- List (Array)
- Tuple (Array)
- Map (Hash)
- Struct (Specialized Map)
- Anonymous Function (Lambda)

!SLIDE 
# Killer Features
- Pattern Matching
- Behaviours & Protocols (For contracts and polymorphism )
- Macros (with easy Access AST)
- Pipe Operator (like in unix bash)
- Syntax niceties
- Property testing (Future feature)
- Elixirscript
- Erlang Interop

!SLIDE shout

# Ok.. But what about our problems?

!SLIDE 
# Problems faced (updated):
Using the Erlang VM with OTP standard eliminates most problems

- <del>Multicore</del>
- <del>Distributed Systems</del>
- <del>Live systems</del>
- Increasingly Complex Systems
- <del>Failure, Failure, Failure</del>
- Rapidly approaching deadlines

!SLIDE
# No really..

<strong>Things provided by the Erlang VM (Beam):</strong>
- Concurrent & distributed by default with Beam process architecture.
- Full core utilization for running processes.
- Ability to connect nodes. When connected they behave as running on single machine.
- Hotcode reloading (absolute zero downtime deploy for nodes).
- Failure handling with OTP standards and practices.

<strong>Things left for developer:</strong>
- Utilization of those tools when designing & building systems.

!SLIDE shout
# Facing Complex systems

!SLIDE

<strong>Functional with Immutability:</strong>
- Modules & Functions
- Very Testable, Easy run in parallel
- Can eliminate side-effects

<strong>Design:</strong>
- Process architecture (True Actor Model)
- Structs (Easily model business domain Datastructures)
- Pattern matching (Handle edge cases without making complex code)

<strong>One Stack:</strong>
- Minimize dependency on other systems

!SLIDE shout
# Facing Deadlines

!SLIDE 

<strong>Batteries included: </strong> hex, mix, iex ++

<strong>Great libraries:</strong> Phoenix, Ecto, Nerves, Credo

<strong>Superb documentation:</strong> ExDoc & Typespecs

<strong> Really helpfull community: </strong> Slack, Forums, GH Issues

<strong>Growth!!!</strong>

!SLIDE 
# Thats all nice and all, but is anyone using it?

!SLIDE 
# Thats all nice and all, but is anyone using it?

Ericsson has been using Erlang for over 30 years.
About 1/3 of all telephone switches in the world run on the Beam (Erlang VM)

WhatsApp has been leveraging the Erlang VM to scale to millions of users.
Billions of messages per day. Peaks reach 342K messages and 230K logins per second,
with 147M concurrent connections. That is before being acquired by Facebook for 19B$

!SLIDE 
# Great, Growing Community

<img src="images/hex_downloads.png" alt="" height="300px"/><br>
Downloads last week 429K <br>
Total: 146M

!SLIDE 
# Where to start?
- Meetup Prag.ex [meetup.com/prag-ex-Elixir-Erlang-Prague](https://www.meetup.com/prag-ex-Elixir-Erlang-Prague)
- Official site: [elixir-lang.org](http://elixir-lang.org)
- (Amazing) Slack [elixir-slackin.herokuapp.com/](https://elixir-slackin.herokuapp.com/)
- [codeschool.com/courses/try-elixir](https://www.codeschool.com/courses/try-elixir)
- Books! [github.com/sger/ElixirBooks](https://github.com/sger/ElixirBooks)
- Workshop!! 2 or 9 Dec.

!SLIDE shout
<img src="images/programming_elixir.jpg" alt="Programming Elixir" height="450px"/>

<br/>
## Notice the author?

!SLIDE shout
# Questions?
