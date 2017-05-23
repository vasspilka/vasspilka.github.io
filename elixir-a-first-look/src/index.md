# Elixir and OTP, a first look. 
by <a href="https://github.com/vasspilka">@vasspilka</a>

!SLIDE shout
# Elixir and OTP, a first look.

<img src="images/elixir-lang-logo.png" alt="" height="200px"/>

## by <a href="https://github.com/vasspilka">@vasspilka</a>

!SLIDE shout
# Quick Background

!SLIDE shout quieter
# José |> Elixir! What is it about?

!SLIDE 
<img src="images/seven_languages.jpg" alt="" height="500px"/>
## Covers: Ruby, Io, Prolog, Scala, Erlang, Clojure, Haskell

!SLIDE quietest shout
# Used 5 criteria to determine the language to use

!SLIDE quietest shout
# Natural Syntax <br/> Fast and Repeatable Dev Cycle <br/> Concurrent and Fast <br/> Metaprogramming <br/> Failure Management

## Functional language with ruby-like syntax running on the battle-tested Erlang BEAM VM

!SLIDE shout quieter
# What is Erlang/BEAM?
## Language + VM, Created by Ericsson in 1986 to support distributed, fault-tolerant, always-up systems

!SLIDE shout
# 1. Basic Types & Syntax

!SLIDE
# Strings & Constants (Atoms)

    iex> my_utf8_string = "hello " <> "Iñtërnâtiônàlizætiøn"
    "hello Iñtërnâtiônàlizætiøn"
    
    iex> String.upcase(my_utf8_string)
    "HELLO IÑTËRNÂTIÔNÀLIZÆTIØN"
    
    iex> :atom
    :atom
    
    iex> Constant == :"Elixir.Constant"
    true
    
    iex> is_atom(true) && is_atom(false)
    true

!SLIDE 
# Numbers

    iex> 1000 == 1_000
    true

    iex> 0.314159e1 == 314159.0e-5
    true

    iex> my_range = 1..5
    1..5
    
    iex> 10 / 5
    2.0
    
    iex> (rem(13, 12) + 2 + div(8, abs(3 - 5))) * round(6.4)
    42

!SLIDE 
# Tuples

    iex> my_tuple = {:ok, "return value", 715}
    {:ok, "return value", 715}
    
    iex> elem(my_tuple, 2)
    715
    
    iex> put_elem(my_tuple, 2, 815)
    {:ok, "return value", 815}
    
    iex> my_elem
    {:ok, "return value", 715}

    iex> my_map = %{:first => "Ted", :last => "Naleid"}
    %{first: "Ted", last: "Naleid"}
    
    
!SLIDE 
# Lists
    
    iex> my_list = [1, 2, 3]
    [1, 2, 3]
    
    iex> my_list ++ [4, 5]
    [1, 2, 3, 4, 5]
    
    iex> [0 | my_list]
    [0, 1, 2, 3]
    
    iex> ex = [{:lang, "Elixir"}, {:creator, "José"}, {:version, 1.4}]
    [lang: "Elixir", creator: "José", version: 1.4]
    
    iex> ex[:creator]
    "José"

!SLIDE
# Maps

    iex> date = %{year: 2017, month: "March", day: "23"}
    %{year: 2017, month: "March", day: 22}

    iex> date.year
    2017

    iex> date[:year] == date.year
    true

    iex> %{date | day: 23}
    %{year: 2017, month: "March", day: 23}

    iex> %{"string" => :val, 7 => 8, &(&1) => "say what?"}
    %{7 => 8, #Function<...> => "say what?", "string" => :val}


!SLIDE

# Structs

    iex> defmodule Person do
    ...>   defstruct first: "Vasilis", last: "Spilka"
    ...> end
    {:module, Person, …}

    iex> %Person{}
    %Person{first: "Vasilis", last: "Spilka"}

    iex> %Person{first: "Vasek"}
    %Person{first: "Vasek", last: "Spilka"}

    iex> %Person{nope: "Bad Field"}
    ** (CompileError) iex:4: unknown key :nope for struct

!SLIDE

# Structs <> extra

    iex> boss = %Person{first: "Ragnaros", last: "Firelord"}
    %Person{first: "Ragnaros", last: "Firelord"}
    
    iex> is_map(boss)
    true
    
    iex> IO.inspect(boss, structs: false)
    %{__struct__: Person, first: "Ragnaros", last: "Firelord"}
    
    iex> defmodule Elemental, do: defstruct [:first, :last]
    {:module, Elemental, ...}
    
    iex> boss = %{boss | __struct__: Elemental}
    %Elemental{first: "Ragnaros", last: "Firelord"}
    
    
!SLIDE
# Sigils
  
    iex> ~w(foo bar baz)
    ["foo", "bar", "baz"]

    iex> ~w(foo bar baz)a
    [:foo, :bar, :baz]

    iex> ~s(String with escape codes \x26 #{"inter" <> "polation"})
    "String with escape codes & interpolation"

    iex> regexp = ~r/foo|bar/
    ~r/foo|bar/

    iex> "foo" =~ regexp
    true
    

!SLIDE 
# Closures

    iex> sum = fn a, b -> a + b end
    #Function<12.90072148/2 in :erl_eval.expr/5>

    iex> sum.(1, 2)
    3
    
    iex> &(&1 + &2).(1, 2) # shortened closure syntax
    3
    
    iex> fun = fn kl -> Enum.reduce(kl, "", & &2 <> elem(&1, 1)) end
    #Function<6.87737649/1 in :erl_eval.expr/5>
    
    iex> fun.(foo: "foo", bar: "bar", bux: "bux")
    "foobarbux"
    
!SLIDE 
# Pattern Matching
    iex> a = {:ok, 1}
    {:ok, 1}  

    iex> {:ok, b} = {:ok, 1}
    {:ok, 1}

    iex> b
    1    

!SLIDE 

# Pattern Matching Lists
    iex> [a, b, c] = [1, 2, 3]
    [1, 2, 3]

    iex> a
    1

    iex> [head | tail] = [1, 2, 3]
    [1, 2, 3]

    iex> head
    1

    iex> tail
    [2, 3]

!SLIDE 

# Pattern Matching Structs

    case HTTP.get(url) do
      {:ok, %HTTP.Resp{ status: 200, body: body }} ->
        IO.puts body
      {:ok, %HTTP.Resp{ status: 404 }} ->
        IO.puts "Not found :("
      {:ok, %HTTP.Resp{ status: status }} ->
        IO.puts "HTTP Status: #{status}"
      {:error, %HTTP.Error{ reason: reason }} ->
        IO.inspect reason
      _ ->
        IO.puts "¯\_(ツ)_/¯"
    end     


!SLIDE

# Even More Pattern Matching

    def execute({:ok, good_value}) do
      IO.puts "Known good value: #{good_value}"
    end

    def execute({:error, error_reason}) do
      IO.puts "Error! #{error_reason}"
    end

    iex> execute({:ok, "Yay!"})
    Known good value: Yay!

    iex> execute({:error, "Boo!"})
    Error! Boo!

!SLIDE 

# Pipe Operator `|>`

Like unix pipe operator, it passes result from 
last method as first argument

    to_string(Enum.reduce(Enum.map([1,2,3], & &1 * 2), 0, & &1 + &2))

    list = [18, 31, 30, 30, 33, 6]
    list = Enum.map(list, & &1 + 5)
    list = List.insert_at(list, 3, 40) 
    list = Enum.map(list, & &1 * 3)

    [18, 31, 30, 30, 33, 6]
    |> Enum.map(& &1 + 5)
    |> List.insert_at(3, 40) 
    |> Enum.map(& &1 * 3)
    
Outputs `'Elixir!'` ⊙.☉ Woot?

!SLIDE quietest
# Concurrency Built-in.

    iex> parent = self()
    #PID<0.90.0>

    iex> spawn(fn -> send parent, "hello world" end)
    #PID<0.93.0>

    iex> receive do message -> IO.puts message end
    hello world
    :ok

## Actor Model

!SLIDE quietest
# Simple Interop with Erlang

<br/>

    iex> :crypto.md5("sekr1t")
    <<192, 151, 240, 131, 252, 86, 1, 90, 71, 171, 2, …

Can easily leverage 30+ years of Erlang libraries

!SLIDE quieter shout
# Metaprogramming!

## How expressive can you make your code

!SLIDE quietest

# Hygenic Macros

    defmacro unless(expr, opts) do
      quote do
        if(!unquote(expr), unquote(opts))
      end
    end

    unless true do
      IO.puts "this will never be seen"
    end

## Most of the standard library is written using macros

!SLIDE 

# Easy Access to AST

    iex> ast = quote, do 2 * 2 / 7
    {:/,[context: Elixir, import: Kernel],
     [{:*,[context: Elixir, import: Kernel], [2, 2]}, 7]}

Underlying AST looks a bit like a lisp

## Full discussion bigger than this presentation, check out "Metaprogramming Elixir", by Chris McCord


!SLIDE shout
# 2. OTP
## Collection of libraries to ease programming distributed applications. Now a common programming pattern.

!SLIDE shout
# Failure Management      

!SLIDE
# Abstractions in Elixir <br/> (Mostly thin wrappers around Erlang/OTP)

 * Application
 * Supervisor
 * Genserver
 * GenStage
 * Agent
 * Task

!SLIDE
# Supervision Trees
<img src="images/hao_01.png" alt="" height="500px"/>

!SLIDE smaller-code

    defmodule SimpleQueue do
      use GenServer

      def start_link(state \\ []) do
        GenServer.start_link(__MODULE__, state, name: __MODULE__)
      end

      def queue,          do: GenServer.call(__MODULE__, :queue)
      def dequeue,        do: GenServer.call(__MODULE__, :dequeue)
      def enqueue(value), do: GenServer.cast(__MODULE__, {:enqueue, value})

      def handle_call(:queue, _from, state), do: {:reply, state, state}

      def handle_call(:dequeue, _from, []), do: {:reply, nil, []}
      def handle_call(:dequeue, _from, [value|state]) do
        {:reply, value, state}
      end

      def handle_cast({:enqueue, value}, state) do
        {:noreply, state ++ [value]}
      end
    end
    
    SimpleQueue.start_link([1,2,3,4,5])
    SimpleQueue.queue  #=> [1,2,3,4,5]


!SLIDE  
# Erlang Activity Monitor

    iex> :observer.start

<img src="images/observer.png" alt="" height="500px"/>

!SLIDE shout quieter
# Great Single-Box Scalability
## Often 100's of thousands to millions of processes per machine <br/> ~2KB of stack/heap per thread

!SLIDE shout quietest
# Most Languages Littered with <br/>Defensive Programming 
## Miss an edge case and your app crashes<br/> ex: Goroutines aren't memory isolated…one dying takes down entire process

!SLIDE shout quietest
# Better Architecture -> Cleaner Code
## Makes developers happy

!SLIDE shout
# Tooling

!SLIDE quietest smaller-code
# Mix Build Tool

    $ mix new myapp
    * creating README.md
    * creating .gitignore
    * creating mix.exs
    * creating config
    * creating config/config.exs
    * creating lib
    * creating lib/myapp.ex
    * creating test
    * creating test/test_helper.exs
    * creating test/myapp_test.exs

    Your mix project was created successfully.
    You can use mix to compile it, test it, and more:

        cd myapp
        mix test

    Run `mix help` for more commands.

!SLIDE quietest smaller-code

# Hex Package Manager
 
    defmodule MyProject.Mixfile do
      use Mix.Project

      def project do
        [app: :myapp,
         version: "0.0.1",
         elixir: "~> 1.4.4",
         deps: deps()]
      end   

      def application do
        [extra_applications: [:logger]]
      end

      defp deps do
        [{:ecto, "~> 0.11.3"},
         {:postgrex, "~> 0.8.1"},
         {:cowboy, github: "extend/cowboy"}]
      end
    end


!SLIDE quietest smaller-code

# `iex` is a Great REPL 

    iex> h Enum.map<tab>
    map/2           map_join/3      map_reduce/3

    iex> h Enum.map/2

                                def map(collection, fun)

    Returns a new collection, where each item is the result of invoking fun 
    on each corresponding item of collection.

    For dicts, the function expects a key-value tuple.

    Examples

    ┃ iex> Enum.map([1, 2, 3], fn(x) -> x * 2 end)
    ┃ [2, 4, 6]
    ┃
    ┃ iex> Enum.map([a: 1, b: 2], fn({k, v}) -> {k, -v} end)
    ┃ [a: -1, b: -2]


!SLIDE

# Debugging via `pry`

    require IEx

    def index(conn, _params) do
      IEx.pry
      conn |> render "index"
    end

Similar to the JavaScript `debugger;` command

!SLIDE
# Deployment

With Erlang/OTP releases

  * Distilery
  * edeliver
  
Hot-code swapping and other Beam goodies

!SLIDE shout
# Solid Documentation

## mix hex.publish docs

!SLIDE shout quieter
# Ecosystem & Community

!SLIDE shout quieter
# #elixir on slack

!SLIDE
Noteable Libraries
  * Phoenix
  * Ecto
  * Nerves Project
  * Absinthe
  
Noteable Projects
  * Firestorm
  * Farmbot

!SLIDE 
# Great, Growing Community
<img src="images/hex_downloads.png" alt="" height="400px"/>
Hex Downloads (from [@emjii](https://twitter.com/emjii/status/613370295618007040) on 2015-06-24)

!SLIDE
# Notable Sites
  
  * https://elixir-lang.org/ Official Elixir Page
  * https://hex.pm/ Official Package Distributor (Also for Erlang)
  * https://elixirforum.com/ Elixir Forum
  * https://elixirstatus.com/ Elixir articles, news, and library updates 
  * https://github.com/h4cc/awesome-elixir Just an Awesome list
  * https://elixir.libhunt.com/ Elixir Library search with categories
  * http://plataformatec.com.br/elixir-radar/jobs Elixir Jobs
  * https://github.com/lexmag/elixir-style-guide Elixir Style Guide
  * https://phoenix-battleship.herokuapp.com/ Battleships!!! (I love this one)
  
!SLIDE

  * https://www.facebook.com/groups/1480245995319184/ Elixir & Phoenix (CZ, SK) by Michal Hantl
  * https://www.meetup.com/prag-ex-Elixir-Erlang-Prague/ prag.ex Elixir & Erlang in Prague
  * http://vasspilka.github.io/elixir-a-first-look/ These slides
  
!SLIDE
# Companies using Elixir

  * Discord
  * Bleacher Report
  * Pinterest
  * Lexmark
  
++ Many more https://devhub.io/repos/doomspork-elixir-companies
  
!SLIDE shout quietest
# Elixir's Strengths<br/><br/>Apps with many connections &amp; high uptime requirements
## (i.e. Internet of Things, REST/socket webservices, Mobile App back-end, Telephony)

!SLIDE shout quietest
# Elixir Weaknesses<br/><br/>Significant Graphics/GUI or Sequential Math
## There are better languages for the next Doom or Bitcoin mining

!SLIDE shout
<img src="images/programming_elixir.jpg" alt="Programming Elixir" height="450px"/>
<img src="images/elixir_in_action.png" alt="Elixir in Action" height="450px"/>

!SLIDE shout
# Questions? 
<br/><br/>
Find me @
https://twitter.com/vasspilka
https://github.com/vasspilka
