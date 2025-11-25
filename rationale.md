# Rationale

Currently *(as far as I'm aware)*, the primary C# IDEs are
[JetBrains Rider](https://www.jetbrains.com/rider/) and
[Visual Studio](https://visualstudio.microsoft.com/), with
[Visual Studio Code](https://code.visualstudio.com/) coming in at a low 3rd
place, based on my own experience, and the experience of others that I have
spoken with. We don't really have any *(high quality)* open-source IDEs for C#,
and well there's a reason for that *(in my opinion)*, primarily, the lack of
*(good)* open-source IDE tools.

There are of course open-source language servers for C# already, primarily
[OmniSharp](https://www.omnisharp.net/) and the
[Roslyn](https://github.com/dotnet/roslyn) based
[language server](https://github.com/dotnet/roslyn/tree/main/src/LanguageServer),
but of course, they have issues of their own *(and quite a few of them).*

## Disclaimer

This document is being written on the 20th of November, 2025 *(and the
surrounding days)*. And as such, the information and opinions shown here are
only relevant on this date, the linked: websites, issues, pull requests, etc
will obviously update at some point in the future, and as such my complaints
may become outdated.

This document **will not** be updated to account for that, this is because this
document is meant to explain the original situation that birthed the Bug.NET
project.

**Additionally**, all of the projects mentioned *(and somewhat roasted)* here
are worked on by actual human beings, with their own: lives, feelings,
weaknesses, strengths, and emotions. They all have different priorities, needs,
and situations, most of them won't even be responsible *(neither directly nor
indirectly)* for the issues that I'm highlighting, in my opinion, the issues are
a consequence of: misguided priorities, project (mis)management, and corporate
greed.

**As such, please DO NOT attack, or harass, or do anything of the sort to the
developers, or to projects that they are working on, or to the other people that
are involved.**


## OmniSharp

I don't like to bad talk other open-source projects, especially ones that
are working hard despite not having all the resources they'd need, however I
do have to point out the difference in priorities, and why Bug.NET was created
instead of just contributing to an existing project.

### .NET Framework

First of, OmniSharp is *still* supporting .NET Framework, which is
extremely outdated, and everything *should* be using .NET Core *(now just
called .NET).* And yes, .NET Framework *is*
[still supported](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-framework)
by Microsoft, however that's pretty much only for corporate users, I
***really*** hope that no hobbyist is still regularly using it without a good
reason.

In *my* opinion, OmniSharp should not be focusing their efforts on supporting
.NET Framework *(and in turn damaging the project - more on this in a
moment),* since as mentioned before, pretty much everything that still depends
on .NET Framework is an outdated corporate environment *(to the best of my
knowledge)*, and they will very likely still be using the proprietary tooling as
part of the organisation/company anyway - but if I'm wrong then please do
correct me.

OmniSharp *is* in fact discussing
[removing .NET Framework support](https://github.com/OmniSharp/omnisharp-roslyn/issues/2647),
but it's moving very slowly, and as
[Joey Robichaud](https://github.com/JoeRobich)
has
[said on a relevant issue](https://github.com/OmniSharp/omnisharp-roslyn/issues/2663#issuecomment-2734776686):

> When I have time to contribute, that is what I will be working towards. I
> would love to think I will get there before .NET 10 is released.

The goal of which has clearly failed *(as .NET 10 has already released, and
there doesn't seem to be obvious any updates about the milestone)*, not to blame
them though, they seem to be quite busy judging by their GitHub contribution
graph.

#### Mono

Now, just a little earlier I mentioned that .NET Framework support is actively
harming the project, so what exactly did I mean by that? Well OmniSharp is still
using [Mono](https://www.mono-project.com) for their Linux/OSX builds, as their
[current primary repository](https://github.com/OmniSharp/omnisharp-roslyn)
states:

> OmniSharp is built with the .NET Core SDK on Windows and Mono on OSX/Linux.

The reason *why* OmniSharp is still using Mono, is because it's still supporting
.NET Framework. So why is this a problem? Well, Mono itself states *(on
[it's website](https://www.mono-project.com))* that it's become obsolete, and
shouldn't be used:

> Microsoft maintains a modern fork of
> [Mono runtime in the dotnet/runtime repo](https://github.com/dotnet/runtime/tree/main/src/mono)
> and has been progressively moving workloads to that fork. **That work is now
> complete, and we recommend that active Mono users and maintainers of
> Mono-based app frameworks migrate to [.NET](https://github.com/dotnet/core)
> which includes work from this fork.**

### Documentation

Now, sadly the .NET Framework support *(and using Mono)* is not the only
problem with OmniSharp. There is also a lack of documentation, and it clearly
doesn't seem like a priority to them, the main example of this that I've found,
is the DAP documentation, on the
[main readme](https://github.com/OmniSharp/csharp-language-server-protocol) of
their LSP implementation they mention:

> For more information about using the DebugAdapterClient / DebugAdapterServer
> on it's own
> [here](https://github.com/OmniSharp/csharp-language-server-protocol/blob/master/docs/dap.md).

However, if you go to that link, you'll be greeted with a completely empty
markdown file, one that's been empty for *5 years* already since it's been
created on the 1st of October, 2020.

### Visual Studio Code extension

As my final point, I'd like to highlight the OmniSharp situation with its
Visual Studio Code extension, which originally, was an OmniSharp project that
was available at
[OmniSharp/omnisharp-vscode](https://github.com/OmniSharp/omnisharp-vscode),
however, if you try going to that repository now, you'll instead be redirected
to the [dotnet/vscode-csharp](https://github.com/dotnet/vscode-csharp)
repository, which is for the official C# extension for Visual Studio Code.

Now at first, there doesn't seem to be anything wrong with this, an official
extension exists, and so it becomes the recommended one, *all is well*... Or so
it seems at least, the official C# extension recommends using the
[C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit),
which is the official Visual Studio Extension for working with .NET and
C#.

For clarification, the C# extension is for the LSP and the language support, the
C# Dev Kit is for all of the other tooling.

The problem with the C# Dev Kit, comes with the debugger, and more specifically,
it's [license](https://github.com/dotnet/vscode-csharp/blob/main/docs/debugger/Microsoft-.NET-Core-Debugger-licensing-and-Microsoft-Visual-Studio-Code.md):

> The C# extension for Visual Studio Code includes the Microsoft .NET Core
> Debugger (vsdbg). Unlike VS Code, and most other parts of the .NET Core
> ecosystem, vsdbg is not an open source product but rather is a proprietary
> part of Visual Studio. It is licensed to work only with IDEs from Microsoft
> -- Visual Studio Code, Visual Studio, or Visual Studio for Mac.

*(More on the .NET debugger situation later).*

As such, OmniSharp has stopped working on it's own product and instead allowed
Microsoft to take over, and make a very important part of it closed-source and
proprietary. Whether that was a reasonable response *(by OmniSharp)* based on
the amount of developer resources available is a different question. The issue
that I'm raising is about the priorities and goals of the OmniSharp project, as
it clearly doesn't seem to be about putting open-source first.

The C# Dev Kit, *does* allow you to still use OmniSharp *(with the
proprietary debugger),* however there still seem to be
[a lot of problems](https://github.com/dotnet/vscode-csharp/issues/5429) with
it.

## The Roslyn LSP

The [Roslyn](https://github.com/dotnet/roslyn) project does offer up its own
[language server](https://github.com/dotnet/roslyn/tree/0dfbd76cfa24436cd456f6dbb73acd1dde4e363e/src/LanguageServer),
however, once again, documentation does not seem to be a priority, and it's also
*very* clearly meant for only being used with Visual Studio and the C# Dev Kit.

### The language server

First off, you'd obviously expect the language server to be downloadable right?
Well so did the person asking this
[Q&A question](https://github.com/dotnet/roslyn/discussions/69731):

> I initially expected the language server to be bundled together with .net sdk,
> but it doesn't seem to be there.
>
> After looking at the
> [project file](https://github.com/dotnet/roslyn/blob/ff8e601c5471f627de2f0e12ef1f4d417200adcf/src/Features/LanguageServer/Microsoft.CodeAnalysis.LanguageServer/Microsoft.CodeAnalysis.LanguageServer.csproj#L21)
> I see that the project gets bundled as a NuGet package, but it's not
> published.
>
> How do I download the language server?

*(The project file link has been updated to the version of the code
available at the time since the current link is broken as the file has been
moved to a different directory).*

Now after asking this question, the response they get is:

> Access the roslyn CI at
> https://dev.azure.com/dnceng-public/public/_build?definitionId=95
> Pick the latest successful run, then you will be able to access the artifacts
> by clicking the "## published" button

So there's two weird things here:

1. The language server doesn't have a proper download, which is obviously not
   very friendly to the people trying to use it, or to the people trying to
   set-up automated updates to newer versions, as you'd be able to do with
   GitHub releases for examples.

2. The language server is packaged as a NuGet package, but it's not actually
   published to [nuget.org](https://www.nuget.org).

The first part certainly shouldn't be difficult to solve, especially for
Microsoft, I mean, *obviously* they've made tons of things easily downloadable.

Now for the second part, I'd link to bring your attention to the previously
mentioned project file, more specifically the comment right above the linked
line *(which is
[still there now](https://github.com/dotnet/roslyn/blob/b9f26f0e3e3b81c8a0ff10449c36f6e579779b82/src/LanguageServer/Microsoft.CodeAnalysis.LanguageServer/Microsoft.CodeAnalysis.LanguageServer.csproj#L10)),*
the comment states:

> Build a nuget package for this project. This is not consumed as a standard
> NuGet package; it just contains the server executables that we need to ship
> **inside the extension vsix**. The extension will download this and extract
> the executables when it builds.  NuGet **just happens to be a convenient way**
> to share build artifacts.

So obviously they don't seem to care about making the language server easily
usable by other people.

Furthermore, the Q&A discussion mentioned earlier mentions a relevant issue:

> We do publish a nuget package (not to nuget.org though).
> See [#71474 (comment)](https://github.com/dotnet/roslyn/issues/71474#issuecomment-2177303207)
> for details.

The linked comment is a little big to include fully so I'll just include the
relevant parts:

1. > we haven't published the packages to nuget.org, but they are available on
     this azdo feed...

2. > The package name is
     `Microsoft.CodeAnalysis.LanguageServer.<platform_name>.` There is also a
     `Microsoft.CodeAnalysis.LanguageServer.neutral` package that should work on
     any platform (though doesn't have heavy testing of it).
   >
   > There is also a `Microsoft.CodeAnalysis.LanguageServer` package, but it is
     no longer updated should be considered deprecated.

3. > If you're taking a dependency on the package, I recommend saving them to
     your own feed as versions are not kept around forever.

So, to explain this in simple terms:

1. the NuGet package isn't published on [nuget.org](https://www.nuget.org), and
   instead it's on a different azure feed.
2. The packages are a bit of a mess, and one package *(the one that would likely
   be the primary package)* isn't even tested properly - not very friendly to
   the developers that would like to use it.
3. The recommended feed isn't even stable *(since it's just build artifacts
   and not an actual feed),* and you'd have to mirror it.

This is all SO INCREDIBLY DEVELOPER UNFRIENDLY. I mean seriously, I'm not sure
if there's *anything* that screams that they don't care about other people
using this language server.

Actually that's a lie, because now we're moving onto the next section of this
document.

### The documentation

So there's still more parts of that previously mentioned
[issue comment](https://github.com/dotnet/roslyn/issues/71474#issuecomment-2177303207):

> We don't have any explicit instructions on consuming the language server,
> but hopefully the C# extension code that consumes it might be helpful
>
> 1. Restoring the packages -
  https://github.com/dotnet/vscode-csharp/blob/main/tasks/offlinePackagingTasks.ts#L71
> 2. Starting the server -
  https://github.com/dotnet/vscode-csharp/blob/main/src/lsptoolshost/roslynLanguageServer.ts#L493

So, not only do they not provide a stable download source for the language
server, they also don't even document how to use it, you're expected to read
through lots of TypeScript code to understand how to use it. Not to mention that
the links you see above are shown exactly as they are in the comment, they're
not permalinks, the actual things they were pointing to were *(as permalinks)*:

> 1. Restoring the packages -
  https://github.com/dotnet/vscode-csharp/blob/d3b97258aacdf1fdc68c6d46b2b966a42d126861/tasks/offlinePackagingTasks.ts#L71
> 2. Starting the server -
  https://github.com/dotnet/vscode-csharp/blob/d3b97258aacdf1fdc68c6d46b2b966a42d126861/src/lsptoolshost/roslynLanguageServer.ts#L493

The first link didn't age that badly *(at least at the time of writing this),*
[it only moved by 2 lines](https://github.com/dotnet/vscode-csharp/blob/9bb8c5018887c7af0e4a2ff0e784dfcf9174cbec/tasks/offlinePackagingTasks.ts#L71)
so it's still in the same area, but the 2nd link... Well the file
doesn't even exist in the same location, so you have to go hunting for it, and
even if you do find the new file location, and then you go to the line the
original link pointed to, you'll be met with a
[completely unrelated area of the code](https://github.com/dotnet/vscode-csharp/blob/9bb8c5018887c7af0e4a2ff0e784dfcf9174cbec/src/lsptoolshost/server/roslynLanguageServer.ts#L493C1-L493C19).
*(Which is why you'd have to look through a lot of TypeScript code if you
decided to not find the actual source they were pointing to)*.

Instead, if you have to look on the main branch specifically, then figure out
which commit was the latest one before the comment was made *(assuming they
didn't draft the comment beforehand and just took a while to reply),* and only
then would you be able to figure out the exact parts that they were point to.

Now of course permalinks *do* have the problem that the code they're point to
could be outdated, but in my opinion making sure the relevant area of the code
is pointed to will at least be a better starting point than a broken link.

And so clearly, the project itself isn't set up to be friendly to the other
developers trying to use the language server, and neither are the developers
working on it *(the latter I could excuse though, they're only human after
all)*.


## The debugger situation

.NET is in an *"interesting"* situation in regards to the debugger, as
mentioned earlier, the main debugger used in Visual Studio and the C# Dev Kit is
vsdbg, which unlike most of the .NET ecosystem is close-sourced and proprietary,
and it's
[license](https://visualstudio.microsoft.com/license-terms/mt644895/)
only allows it to be used in the Microsoft versions of Visual Studio and Visual
Studio Code:

> You may only use the .NET Core Debugger Components with Visual Studio Code,
> Visual Studio or Xamarin Studio software to help you develop and test your
> applications.

I'd recommend reading the following GitHub issues for: more context; for seeing
how other people feel about this; and to see how long they've been complaining
about this, without any official word from Microsoft or any of the .NET teams
*(as far as I can see).*

- [dotnet/core/4788](https://github.com/dotnet/core/issues/4788)
- [dotnet/core/505](https://github.com/dotnet/core/issues/505)
- [dotnet/vscode-sharp/1059](https://github.com/dotnet/vscode-csharp/issues/1059)

Clearly, Microsoft is scared of something, after all, pretty much almost
everything else in the .NET ecosystem is open-sourced, and benefits from a large
community working on it. The only things that have ever been proprietary and
required payment were extra features that were a part of the "Professional" and
"Enterprise" versions of Visual Studio, and were not present in the "Community"
edition, for a full list take a look at the
[Visual Studio comparison page](https://visualstudio.microsoft.com/vs/compare/).

Quite clearly, it makes sense to pay wall the features listed here, they're
extra premiums that are not required for general development, but a debugger? A
bog-standard debugger. That's something pretty much every developer would
consider a basic feature for development. *(Not counting the hubris of the
young, self-declared geniuses that are certainly under the
[Dunning-Kruger effect](https://en.wikipedia.org/wiki/Dunning%E2%80%93Kruger_effect))*.

### JetBrains

So, JetBrain's Rider is clearly a very popular option that people use, and
people are able to debug their C# programs there, so how does JetBrains do it?
Well as it turns out, at first *(according to their
[EAP 17 blog post](https://blog.jetbrains.com/dotnet/2017/02/15/rider-eap-17-nuget-unit-testing-build-debugging/#debugging-bad-news-about-coreclr)),*
they were *(unknowingly)* breaking the license of vsdbg:

> We were using this functionality considering it part of .NET Core which is
> Open Source, but it turned out that this specific package
> [has a different licensing model](https://visualstudio.microsoft.com/license-terms/mt644895/).

However, only 8 days after, JetBrains has released their
[EAP 18 blog post](https://blog.jetbrains.com/dotnet/2017/02/23/rider-eap-18-coreclr-debugging-back-windows/#debugging-good news-about-coreclr-on-windows),
in which they state that they've managed to bring back debugging support, most
certainly through their own debugger:

> CoreCLR debugging on Windows is back! (Linux and Mac OS X will come later)

Now I'm assuming that this debugger was still quite rudimentary, considering it
was only made in ~8 days *(potentially more if they waited before making the
first blog post)*, and they obviously would've worked hard to improve it from
that point, however I do not have first-hand experience of what it was like at
the time *(I would be interested to hearing about it though if anyone has
had experience with it)*.

However, since it *is* a JetBrains product, their own debugger is also
close-sourced and proprietary.

### Samsung

Now enter Samsung, which has been *(and still is - somewhat)*, developing an
open-source .NET Core debugger, that they dubbed
[netcoredbg](https://github.com/Samsung/netcoredbg), this is the primary
alternative I hear of when it comes to .NET debuggers, and there have been forks
of the C# Dev Kit that use this debugger instead of vsdbg.

So far all seems good, however, *sadly*, netcoredbg is still missing some
*very* useful features, such as:

- [Samsung/netcoredbg/142](https://github.com/Samsung/netcoredbg/issues/142) -
  No support for the [`DebuggerDisplayAttribute`](https://learn.microsoft.com/dotnet/api/system.diagnostics.debuggerdisplayattribute),
  which is very useful in my experience.
- [Samsung/netcoredbg/85](https://github.com/Samsung/netcoredbg/issues/85) - No
  support for displaying collections, which is also incredibly useful.

It's also been a year since the last release, and
[the last commit](https://github.com/Samsung/netcoredbg/commit/83214c3993c052a0ccb8854b913e028c5e365bc6).
According to a recent
[issue](https://github.com/Samsung/netcoredbg/issues/208), the project is still
being worked on, with a new release hopefully coming before the end of the year:

> We plan to make a new release later this year, which will include community
> PRs that are already approved, as well as .net 10 support.

Now, the *(initially)* confusing part is that the latest commit is a year old,
and that there's a ton of unmerged *(but closed)* pull requests, yet apparently
there's going to be a new release soon-ish?

So what's going on here? Well after looking for a bit I have found this
[pull request comment](https://github.com/Samsung/netcoredbg/pull/176#pullrequestreview-2328495859):

> Thanks for your contribution! This change is already merged in internal dev
> repo, will be available in upstream on next repo sync.

So it sounds like the Samsung developers have their own internal repository that
they use for working on the project, which is then *(infrequently by the looks
of it)* mirrored to the public GitHub one. This isn't very contributor friendly.
Although they do seem to have accepted some pull requests, an exact number is a
bit annoying to figure out since the pull requests are closed, not merged, and
not all of the approved ones are actually marked as approved by a reviewer, but
instead there's just a comment left by a maintainer approving the pull request.

Obviously this approach sounds like it would put a lot more strain on the
Samsung developers, since they'll *(possibly)* have to be resolving a lot of
merge conflicts since all of the pull requests are based on an outdated version
of the main branch *(since the up-to-date one is internal, and not publicly
accessible).*

Additionally, and this might just be my own bias here, but the Samsung debugger
is written in C++, and well, clearly the people that would most want a .NET
debugger are .NET developers *(most of whom will primarily be C#
developers)*, and I, as a C# developer, most certainly *do not* want to be
working with C++, or it's messy build system. Which is why the Bug.NET debugger
is going to be written in C#, so that fellow C# developers have a much easier
time contributing, or modifying the project.


## Conclusion

Now, hopefully you can see and understand the sort of weird situation the .NET
tooling is in, and why this project has been started.
