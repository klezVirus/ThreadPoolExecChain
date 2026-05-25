# ThreadPoolExecChain 

Simple POC to chain multiple callbacks via tail calls to artificially build a callstack

## TL;DR

ThreadPoolExecChain is a simple proof of concept demonstrating how multiple callbacks can be chained via tail calls to artificially construct a call stack, and how specific return-value–saving frames can be leveraged to recover the results of the last target call.

**Read more in the Blog Post:** [Callback hell: abusing callbacks, tail-calls, and proxy frames to obfuscate the stack](https://klezvirus.github.io/posts/Callback-Hell/). 

## Overview

This repository demonstrates a PoC implementation to construct a semi-artificial (callback-dependent) call stack when calling arbitrary Windows APIs, while simultanously save the return value of the called Windows API. 

An extensive overview of the technique and why it was developed can be read [here](https://klezvirus.github.io/posts/Callback-hell/).

This POC was made to work with a few callback-chains to test its flexibility but should be customized for additional results. Moreover, 
the gadget chosen to save the return value cannot be used to execute functions with more than 4 arguments (technically 5, but you'll lose a volatile register in the process and that's not recommended).

## Previous Work 

* [Hiding In PlainSight - Indirect Syscall is Dead! Long Live Custom Call Stacks](https://0xdarkvortex.dev/hiding-in-plainsight/)

## Credits

* [namazso](https://x.com/namazso): stack unwinding inner mechanics, retaddr/frame spoofing, and more
* [Chetan Nayak](https://x.com/NinjaParanoid): previous public work on implementing ThreadPool Worker Callback as a tailcall
* [trickster](https://x.com/trickster012): for giving me a reason and a motivation to rework on this
