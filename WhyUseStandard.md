## Must Read ##
We use very specific versions of software and **strongly** recommend you don't expose yourself to almost certain failure by doing things differently initially.

You can get your feet wet by spinning up an [Amazon instance](AmazonInstance.md) or running a [VM](VMInstance.md) regardless of what hardware and OS you use.

Even if your end goal is to run BabelRoom in a different environment the first step should involve getting a standard instance running -- if only for reference.

## Background ##
BabelRoom server is cloud based. This implies the same _server image_ will be run on tens to thousands (and sometimes more) instances.

It's simply not possible to deploy at these scales unless every instance is an exact clone of every other. Every misconfiguration and bug needs to be applicable to every instance so lessons learnt on one can be used to fix them all.

So even if you only intend running a single server instance bear in mind that the software, packaging and setup scripts were all designed with the goal of achieving an exact version of every piece of software in the server.

With that context in mind, consider:

  * The process to install BabelRoom is designed to render exact versions (down to the patch level) of every component from kernel to application. A change in a single component would likely cause the entire install to fail. Stated another way, the installation processes are not geared towards a la carte packaging.

  * If you succeed in completing the installation there would be practically no support for the end result. Because a bug could be the indirect result of a complex interplay with other components your environment could not be compared in an apples-to-apples fashion with that of any other person. Stated a different way: everybody will assume your issue is a result of the differences in environment and they would likely not invest time in helping you beyond general pointers.

  * Your experiences would likely not be usable by the community in general and we'd miss an opportunity to grow our knowledgebase.