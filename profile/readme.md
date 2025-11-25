# Bug.NET

Bug.NET *(originally "bugnet" - a name picked out for a .NET debugger - but
the [name was taken](https://github.com/bugnet) on GitHub)* is a child
organisation of [OwlDomain](https://github.com/Owl-Domain) that is responsible
for creating a collection of open-source tools and components intended to be
used when creating .NET IDEs and extensions.

*(Some of our projects will be helpful when creating general IDEs and text
editors, not just the ones meant to be used for .NET)*.


## Current projects

- A Bug.NET command line utility which will serve as an *(optional)* entry
  point for invoking all of the other Bug.NET tools.
  [Repository](https://github.com/BugDotNet/cli) |
  [Project](https://github.com/orgs/BugDotNet/projects/3).
- A .NET debugger written in C#.
  [Repository](https://github.com/BugDotNet/debugger) |
  [Project](https://github.com/orgs/BugDotNet/projects/2).
  - A sub-project for a reusable DAP implementation.
  [Repository](https://github.com/BugDotNet/dap) |
  *Project is shared with the debugger above*.


## Roadmap

The current priorities of Bug.NET are *(roughly)* as follows:

1. Create a .NET debugger in C# with
   [DAP](https://microsoft.github.io/debug-adapter-protocol/) support.
2. Create a .NET profiler in C#.
3. Create a .NET language server in C# with
   [LSP](https://microsoft.github.io/language-server-protocol/) support.
4. Add in [LSIF](https://microsoft.github.io/language-server-protocol/specifications/lsif/0.5.0/specification/)
   support.
5. Investigate creating a build server in C# with
   [BSP](https://build-server-protocol.github.io/) support.
6. Plan out which IDE components Bug.NET should focus on creating *(this will
   likely include a performant text editor component)*.

This is just a rough outline so far, and things may change, the current
priority is also on ensuring that C# is supported.


## Rationale

This organisation was created for the sole purpose of solving one problem,
to level the playing field and make it easier for people to create .NET IDEs
that can actually rival the primary *proprietary* ones people are "forced" to
use if they're even remotely serious about their projects.

If you'd like to learn more about what drove us to this, then go ahead and read
the full [rationale document](https://github.com/BugDotNet/.github/blob/main/rationale.md).


## Goals

The Bug.NET project will strive to create a collection of high-quality,
open-source .NET IDE tools and components, while focusing on a highly polished
end product that will level the playing field and help other developers create
products that can rival the current primary proprietary projects.

We will strive to make sure that our projects are fully documented, easy to use,
easy to build, and that they cover different use cases, making things available
as both library packages, and as pre-built command line utilities that are
available on their own, and as part of the Bug.NET
[command line utility](https://github.com/BugDotNet/cli).


## Support

If you've ran into a problem with one of our projects *(or our organisation in
general)*, then please take a look at our
[support guide](../.github/support.md) to learn about the best way to get help
with your issue.


## Contributing

There are many different ways in which you can contribute and help the Bug.NET
project, if you'd like to learn more then take a look at our
[contributing guide](../.github/contributing.md).


## Governance

[Nightowl](https://github.com/nightowl286) will be lead the Bug.NET project as a
"[benevolent dictator for life](https://en.wikipedia.org/wiki/Benevolent_dictator_for_life)",
meaning that they will have the final say about all project decisions and
disputes. If you'd like to learn more then please read our
[governance](../.github/governance.md) document.


## Code of conduct

Everyone participating in the Bug.NET projects, or in our community must follow
our [code of conduct](../.github/code_of_conduct.md).


## Socials

[<img src="https://img.shields.io/discord/1411024983550853162?style=social&logo=discord&label=discord&link=https%3A%2F%2Fdiscord.gg%Eq2mKjcUw5" alt="OwlDomain Discord server badge">](https://discord.gg/Eq2mKjcUw5)

### Discussions

The main community interactions for Bug.NET are happening on the
[discussions](https://github.com/orgs/BugDotNet/discussions)
area of the organisation.

*(All Bug.NET projects share the same discussion forum for ease of use).*

### Discord

The Bug.NET organisation has a dedicated section in the
[OwlDomain discord server](ttps://discord.gg/Eq2mKjcUw5),
you can use it to talk about Bug.NET projects or just about Bug.NET in general.

Feel free to participate in and interact with the wider OwlDomain community
as well!


## Logo

The current logo is a
[Pixabay art piece](https://pixabay.com/vectors/ladybug-ladybird-nature-insect-bug-476344/)
that was quickly modified to include the typical .NET purple color,
if you'd like to suggest a new logo then go ahead and talk about it in the
[new idea discussion](https://github.com/orgs/BugDotNet/discussions/categories/ideas)
area.

Since the current logo does not have its own custom design yet, we'd like to
ask you to refrain from sharing it until an official Bug.NET logo is created.
