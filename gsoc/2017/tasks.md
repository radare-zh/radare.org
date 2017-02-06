# Microtasks

It is strongly recommended that students who want to apply to the radare2 GSoC/RSoC projects will perform a small tasks, to get the idea of students’ capabilities and make them familiar with radare2 codebase, structure and development process. Here is the list of such “qualification” tasks:

### INDEX

## Improve analysis

The current code analysis have many little caveats and issues which may be good to be addressed, fixing them and writing more tests is very important to stabilize and enhance it.

[See these issues](https://github.com/radare/radare2/issues?q=is%3Aissue+is%3Aopen+label%3Aanal)

## Node groups

Being able to select multiple nodes in the graph and group them to colorize them and specify a name for them.

## Smarter lines in graphs

Avoid overlapping edges, currently the ascii art graphs does not overlap nodes, but some edge lines are passing thru.

## Save/restore graph state

This task is necessary when node grouping or layout have changed, this information can be stored in projects by just reusing the `agn` and `age` commands to recreate a graph and feeding the body of the nodes in base64.

## Lua bytecode
Add disassembler, assembler and analyzer for the latest LUA vm.

See [Issue #3836](https://github.com/radare/radare2/issues/3836)

## Python bytecode
See [universal python disassembler](https://github.com/evanw/unwind) for example and [Issue #4228](https://github.com/radare/radare2/issues/4228) for current state of it.

## Improve ragg2 compiler
Ragg2 - simplistic [compiler for C-like syntax](http://radare.today/posts/payloads-in-c/) into tiny binaries for x86-32/64 and arm. Programs generated by ragg2 are relocatable and can be injected in a running process or on-disk binary file. Fixing [ragg2 issues](https://github.com/radare/radare2/issues?q=is%3Aopen+is%3Aissue+label%3Aragg2) will help a lot for creating small payloads for exploiting tasks.

## Better PE (Portable Executable) format support
There are lot of missing features in the current PE file parser. [Here](https://github.com/radare/radare2/issues/921) you can find a full list of those. Implemeting it will help for radare2 usage in malware analysis.

## PCAP loading support
Add pcap support. [See issue](https://github.com/radare/radare2/issues/3574)

## Sdbtization
Radare2 is being slowly refactored to store all the information about session, user metadata and state of debugger in the [SDB](https://github.com/radare/sdb) - simple key-value database. This work still ungoing. So helping us with a few sdbtization bugs will introduce you into the radare2 codebase structure.
[See issues](https://github.com/radare/radare2/issues?q=is%3Aopen+is%3Aissue+label%3Asdbtization)

## ESILization
Radare2 has its own intermediate language - ESIL, but not yet support it for all architectures. So
the task is to add ESIL support to any architecture, which doesn't has it yet.
[See issues](https://github.com/radare/radare2/issues?utf8=%E2%9C%93&q=is%3Aissue%20is%3Aopen%20label%3Aesil) for the related bugs.

## UTF-8 support everywhere

This task requires implementing proper support for multibyte characters in RConsCanvas in order to render UTF-8 characters in the graphs for having better ascii-art boxes and lines.

[Issue #2091](https://github.com/radare/radare2/issues/2091)
[Issue #2032](https://github.com/radare/radare2/issues/2032)
[Issue #4997](https://github.com/radare/radare2/issues/4997)

## Better support for AOT and ART binaries

Current version of r2 is able to load ART and AOT binaries, but we are not yet able to extract all the information that lives in there

## Better support for DEX

Multidex is not yet supported, and there are some specially crafted dex bins that will not load properly. This task requires writing tests, checking with fuzzed and obfuscated dex binaries and fix the bugs found in the process.

## Better support for Dalvik

There are some bugs in the current disassembler that will be good to address them. Also, it will be good to have a dalvik assembler for binary patching.

## Better support for Activities and Permissions (list them, references, etc)

Take ideas from Androguard, and be able to follow execution flow paths to understand which permissions are used in a specific region of code, how to reach a specific activity, etc.

## Fix dyldcache (already listed in fatmacho task)

Dyldcache for user libraries and kernel modules is already supported, but it is not working because of the api changes in RBin. This task implies writing tests for dyldcache (we need to cook a dyldcache that can be distributable, not the ones from Apple). And fix the rbin api to get this working.

## Support remote iOS debugging

Support gdb:// against apple’s debugserver. This feature already works for i386 simulator, but fails when using arm/arm64 backend on real hardware).

## Support to spawn Apps, not just programs
See `debugserver -x springboard` and such to spawn apps from the backboard otherwise they get killed.

