
# TinyJ

TinyJ is not yet-another Java-framework, it is a collection of java libraries
sharing not interfaces and classes but concepts. The main objective is to
provide independently usable artifacts covering many of your daily java needs.


## Goals

### Choice of weapons

It should up to you to decide which parts of TinyJ you want to use.


### Express yourself

TinyJ aims to help you to express your self easily yet concisely in java code.


### Connect

Integrating TinyJ into you code and connecting it to third party libraries
should be easy and non intrusive.


### Being understood

TinyJ aims to keep it's own codebase readable and comprehensible.


### Small footprint

As the name suggests, each TinyJ project aims to keep it's footprint small.
This encompasses artifact size, memory and cpu usage. Obviously there will be
trade-offs. As for artifact size this means well below 1Mbyte.



## Concepts

### KISS

#### simple scope
Each TinyJ project covers a very specific use case giving you the choice of
what to take and what to leave. This also helps to keep the TinyJ codebase the
modular and comprehensible.

#### simple usage (aka no magic)
TinyJ tries not to be smart about what you want. Instead it tries to give you
the means necessary to express your self easily yet concisely.

#### simply readable
TinyJ code should be readable and easily navigable.


### Integrable but not integrated

Integration should happen as much high level as possible, again leaving as
much room for choice as possible. To make that feasible TinyJ tries hard to
make integration as seamless and painless as possible and to keep third party
libraries out.



## Principles

### soLid

The [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))
principles shall apply to all of TinyJ's codebase with a strong emphasize on
Liskov's substitution principle. It's awesome. Really, it is.


### Use standard components

Java's JRE is rich with abstractions and interfaces readily available in
(almost) every java based project. TinyJ builds on top of that wherever it
can. This keeps integrating TinyJ simple and seamless.

And if the JRE is not enough there are even more in the  `javax` namespace.


### Lambda integration

Java 8 lambdas are just giving us a neat syntax for defining inline functions,
they give us also a very useful tool to integrate things based on concepts
instead of interfaces by adapting functional interfaces on the fly.

An example:
```java
interface TinyJApi {
  @FunctionalInterface interface IntAccepter {
    void acceptThatInt(int i);
  }
  void aFunction(IntAccepter in);
}

interface ThatOtherApi {
  @FunctionalInterface interface IntTaker {
    void takeThatInt(int i);
  }
  IntTaker thatOtherFunction();
}

class MyCode {
  TinyJApi tinyJApi;
  ThatOtherApi thatOtherApi;

  void bringingThingsTogether() {
    tinyJApi.aFunction(
      thatOtherApi.thatOtherFunction()::takeThatInt);
  }
}
```

It doesn't get easier than this and obviously it just works the other way
around. And by the way, the `@FunctionalInterface` annotation in purely
optional here and with code completion you don't even have to remember that
```takeThatInt``` bit.

TinyJ enables this integration pattern by using
functional interfaces whenever it's sensible.


### Clean code

TinyJ's codebase tries to follow the rules from
["Clean Code"](https://books.google.com/books/about/Clean_Code.html?id=dwSfGQAACAAJ "Clean Code @ books.google.com")
as faithful as possible.


### Tested

Everything released from TinyJ passed a carefully created test suite.
Bugfixes should include new tests, linked to the github issue, proving that
the Bug is gone.


### Semantic Versioning

Being committed to standard components and keeping things simple TinyJ needs
to break things from time to time (like whenever there is a hot new Java
version) in order provide new features and improve on those upstream changes.
[Semantic Versioning](http://semver.org) is used to communicate such changes.

There will be bugfix releases for previous major versions as time permits.
Within a TinyJ project different major releases are treated as independent
codebases sharing a common goal and mindset.


### Shade

Sometimes there is the really nagging desire to use some small third party
library (like TinyJ :) ). By shading these dependencies TinyJ keeps you
blissfully unaware of such internal details.



## Things to come

### tinyj-web-mvc (~32Kbytes)

TinyJ will start soon (before end of March 2016) with yet another Web MVC
implementation. It's in polishing now so stay tuned.


### tinyj-test-servlet (~16Kbytes)

Mock implementation for HttpServletRequest and HttpServletResponse. A preview
will accompany the tinyj-web-mvc release as it's used in the testsuite.


### tinyj-web-server (in planning)

Finding that tinyj-test-servlet HttpServletRequest an HttpServletResponse
implementations give you almost everything needed to implement the HTTProtocol
let's lift that into a minimal viable HTTP server implementation (may
optionally be accompanied with tinyj-web-mvc).


### tinyj-di (in planning)

Inspired by [TinyDI](https://github.com/jonaash/tinydi) tinyj-di aims to be
yet another [JSR 330](https://jcp.org/en/jsr/detail?id=330) implementation.



## License

If not stated otherwise all files are released under the terms of the Apache
License 2.0. You may not use any file except in compliance with the License.
You may obtain a copy of the License at

<http://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
