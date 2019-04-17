# Language for ML and robotics

## How the world looks like today

### Languages for machine learning

It's no secret that today, Python is by far the most popular language for machine learning and scientific computing.

This has mostly been driven by decades of effort into the ```numpy``` and ```scipy``` ecosystems. The very first commit to ```numpy``` seems to have been made in [2002](https://github.com/numpy/numpy/tags?after=v0.2.2).

While both libraries having Python bindings, a big chunk of them is written in ```C``` with the idea being you get the convenience of ```Python``` with the speed of ```C```

```
git clone https://github.com/numpy/numpy
cloc numpy
```


When deep learning became popular we saw the rise of many deep learning libraries such as ```Pytorch``` and ```Tensorflow``` which also became much more popular than the scientific libraries that inspired them. These two projects are backed respectively by Facebook and Google which means there is an immense amount of resources put here to capture developer mindshare and setup integrations into cloud services.

### Languages for robotics

## What are some good alternatives?

### What do we need from a language for robotics and ML
Before we discuss the alternatives we have at our disposal, it's worth thinking about what exactly we'd like out of a language
1. Easy: we want our language to be ergonomic and easy to use. We don't want to be hacking together several interfaces from several different languages to get the most basic example working.
2. Extensible ecosystem: A lot of libraries are pretty new so it's important that we can contribute to them with minimal overhead and be plugged into a larger ecosystem of developers we can learn form.
3. Fast and small memory footprint: Ultimately we'll be running thousands of simulations of agents acting in games and robots doing stuff. We'll be writing environments from scratch and  we want to be able to experiment without having the same compute budget as Open AI.
4. Safe: We don't want our robots to have undefined behavior since that's just plain dangerous for a physical robot
5. No runtime errors: When we deploy our robots we want them to go about their happy lives without worrying about whether they'll crash

### Great, what are our concrete options
* Python: ticks a lot of boxes but the main issue is because most of the performance sensitive code is written in ```C``` or ```C++``` it's very hard to contribute since it's hard to avoid segfaults and race conditions 
* C/C++: pretty popular in the robotics community but not so much in the ML community. Writing good ```C++``` is hard because memory management is hard and the language doesn't provide good native facilities to reason about it, the language isn't used very much by practicioners but is used by infra teams at big tech companies so it's a reasonable language to pick for use cases.
* Haskell: nice abstractions but suffers from bad performance. I've found Haskell to be more useful to experiment with ideas as opposed to writing libraries.
* Julia: I've been following Julia closely and I feel like they get a lot stuff right, they promise a Python like interface with C like performance. The Julia team has also been early proponents of differentiable computing. While I'm pretty bullish on Julia for numerical computing and machine learning, I'm not so convinced it's suited for systems level programming which we'll need if we're building robots.  
* Rust: provides memory safety and speed. Rust was born as a systems programming language 

## Drumroll 
For this book we're choosing to go with **Rust** because we a fast, safe and productive language.


* All pipeline errors are type errrors
* Runtime errors cost money and are more costly to debug
* Types making contributing to a new codebase easy
* Guarantees of safety make it easy to change a part of a codebase without breaking the rest of it