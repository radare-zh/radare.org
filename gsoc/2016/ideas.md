# Project Ideas




### INDEX

## Web interface
Radare2 has a nice [web interface](http://cloud.rada.re/p) (and not only one: /p, /m and /t), but it's not currently as complete as the command line one. While the later is more powerful, it has a steep learning curve, and it not usable on every devices (Like cellphones or tablets); this is we'd like to put some efforts into an awesome and good-looking web interface.

### Tasks
1. Implement/enhance widgets like:
   - Hexeditor : view and edit, columns should be configurable.
   - Graph : Interactive basicblocks/functions/bindiff graphs.
   - Sections : Memory ranges with attributes.
   - Search : Strings, opcodes, ...
   - Structures : Edition, view, manipulation, â€¦
   - Functions : Edition, view, manipulation, arguments, XREF, ...
2. Make it [responsive](https://en.wikipedia.org/wiki/Responsive_Web_Design)
3. Make it more keyboard friendly (aka-olly)
4. Better Interface for the debugger
   - Panels with list of breakpoints
   - Backtrace with clickable offsets
   - Register panel
5. Optimize it, compress JS, reduce AJAX queries, make it usable on all devices

### Skills
The student should be comfortable with modern web technologies like javascript and HTML5. They don't need to be Ã¼ber-comfortable with C nor assembly, since all the information is obtained directly from radare2.
As a bonus point it would be interesting if they know some basic assembly.

### Difficulty
Easy. If the student if comfortable with web technologies, there shouldn't be any major challenges

### Benefits for the student
The student will gain experience in writing rich web applications, and domain-specific user interface. Also, the student will learn to design usable APIs, since this task will deal with interfacing C and Javascript.

### Benefits for the project
Since radare2 has a steep learning curve, this task will lower the barrier for transitioning from IDA to radare2.

### Assess requirements for midterm/final evaluation

### Mentors
pancake

### Links/Resources
- The [current](http://cloud.rada.re) web interface
- [Announcement](http://radare.today/the-new-web-interface/) of its release
- [Related issues](https://github.com/radare/radare2/labels/webui) on github

## Completing Radeco
radeco, a radare2 based decompiler, was a project that was started in GSoCâ€™15. Currently, radeco features a ESIL to SSA IL converter and a  few optimisations to the IR. The task for this year is to complete the first iteration of the decompiler. This involves several tasks which are listed below. Note that some of these tasks are large and are listed to give students a complete view of the requirements of this project. A potential student is required to discuss these with the mentors and pick some tasks to write their proposals for GSoCâ€™16. Being a relatively new project under the radare banner, this project also gives student an opportunity to learn, design and discuss the architectural aspects of the project.

### Tasks
 - SSA to higher level pseudo/C code writer. This task is the highest priority as it would give us a chance to evaluate the quality of the produces code, receive feedback from the community and aim our efforts in the improving the same in further iterations.
 - Control graph restructuring and reshaping
 - Type inference
 - Some more analysis based on the intermediate language such as type propagation
 - Improvements to the current intermediate representation. The current internal representation for the intermediate representation is not readable by humans (see link). It would be nice to have a text based intermediate representation for debugging and interoperability with other tools.
 - Continuing on the same lines of the previous task, it would be nice to layout graphs like a CFG. The current dot emitter gives complete freedom to graphviz to layout the graph, which results in sub-optimal layout of the graph. This task is to improve this and make it more intuitive and readable.
 - Setup a primitive logging framework for radeco. This allows us to debug and follow the steps of the decompiler easier in order to reason about the process and perform optimisation (not just time but also quality of the output).
 - Full integration with radare2 shell. This shell should allow users to interact with the entire decompilation process and modify any stages if necessary. Additional features like graph colouring / marking would also be a nice bonus.
 - Port some basic analysis such as function recognition from radare2. radeco is in a much better place to implement such analysis. It would be better to implement this in radeco so that we do not have to depend on radare2 for function recognition and also return the results back to radare2.

Additionally, the students are also expected to detail their architecture (in the wikis) and write tests and documentation for any features that they contribute.

### Skills
Knowledge of working of compilers and program analysis (or an interest to learn these quickly)
Some knowledge of rust is an added bonus. A potential student must be willing to learn rust in order to contribute to this project.
Some knowledge of common ISA such as x86, x86_64, ARM.

### Difficulty
Advanced

### Benefits for the student
- General idea about compiler/decompiler working model
- Usage of the Intermediate Languages
- Binary code analysis

### Benefits for the project
Finally, radare2 will have its own retargetable decompiler, which will cover a wide range of architectures

### Assess requirements for midterm/final evaluation
Midterm will be successful, in case of working pseudo/C emitter.
Final term will require working type inference, with tests.

### Links/Resources

- https://github.com/radare/radeco-lib
- https://github.com/radare/radeco-lib/issues

## Better support for UNICORN  debugging
Current support of UNICORN in r2 is more or less a proof of concept. We need to support more architectures, better handle syscall tracing, share memory and initialize/store/restore debugging states from core files, etc. All those features should be a laa par of using ESIL for emulation, which is currently working way better than UNICORN, but having more backends also benefits the overall interface and internal apis.

### Tasks
1. Support more architectures in the unicorn plugins
2. Share memory changes in realtime between r2 io and unicorn process

### Skills
C

### Difficulty
Medium

### Benefits for the student
### Benefits for the project
### Assess requirements for midterm/final evaluation

### Mentors
pancake

### Links/Resources

## Function argument detection
Radare2 doesnâ€™t deal very well with argument and variable and function definition. The student will have to combine several concepts/modules within radare2 to be able to complete this tasks: 
 - Radareâ€™s type system
 - SDB, the internal database format
 - pf, the structure module
 - The analysis engine

![How it looks](https://cloud.githubusercontent.com/assets/1408600/13150924/14752dfa-d668-11e5-869f-32d10f3a8b4a.png)

### Task
 - Add precompiled headers in sdb file for windows OS [#3654](https://github.com/radare/radare2/issues/3654)
 - Autoload those types when `e asm.os = windows`
 - Add "return type" in the Functions definition files to be able to deal with non-return function as well [#3632](https://github.com/radare/radare2/issues/3632)
 - Use Native types instead of pf types in Functions definition files
 - Enhance naming convention and storage to handle types with names composed of multiple words
 - Enhance current display (maybe reuse the e asm.calls display)
 - Changing easily the call convention
 - Add support for windows-x86-32/64
 - Add support for linux-x86-32 functions since some of them have already been added => https://github.com/radare/radare2/blob/master/libr/anal/d/linux-x86-32
 - Add support for linux-x86-32/64
 - Add support for  osx-x86-32/64
 - Add support for naming local variables based off esp [#3735](https://github.com/radare/radare2/issues/3735)
 - Ability to load/export IDA TIL Files
 - Add display stack frame of a function
 - Seamless integration with **asm.emu/asm.emuwrite** display

### Skills
The student should be comfortable with the C language, know the basics of assembly and have knowledge in program analysis.

### Difficulty
Medium

### Benefits for the student
General idea about various platforms ABI

### Benefits for the project
The completion of this task would greatly improve radare2's analysis capabilities, making it ever more competitive with IDA Pro.

### Assess requirements for midterm/final evaluation
At the midterm student should have a working

### Mentors
pancake
xvilka

### Links/Resources
- https://github.com/radare/radare2/issues/3655

## Ropchain generator with ragg2

Since modern architectures are now enforcing [W^X](https://en.wikipedia.org/wiki/W%5EX), exploiters are using [ROP](https://en.wikipedia.org/wiki/Return-oriented_programming). (Un)fortunately, building rop chain by hand can be tedious, this is why some tools can be used to ease this construction : ImmunityDBG has [mona.py](https://www.corelan.be/index.php/2012/12/31/jingle-bofs-jingle-rops-sploiting-all-the-things-with-mona-v2/), there is also [ROPgadget](http://www.shell-storm.org/project/ROPgadget/) and [dropper](https://github.com/rizlik/dropper). It's a shame that despite having [ESIL](https://github.com/radare/radare2/wiki/ESIL), radare2 doesn't have something similar yet.

### Task
1. Implement a "classic" (`/bin/sh` for example) ropchain as a proof-of-concept, like what [ROPgadget](https://github.com/JonathanSalwan/ROPgadget) does. This can be done is almost any language, thanks to the bindings/r2pipe.
2. Caching rop gadgets in SDB, for quicker retrieval
3. Implement a ropchain generator that uses ragg syntax, or something like:
```
register reg1 = 0; 
register reg2 = whatever;
register reg3 = reg1 + reg2;
system(echo reg3);
```

### Skills
The student should be comfortable with the C language, know some assembly and a high-level language. Also, knowing a little bit of automatic binary analysis wouldnâ€™t hurt.

### Difficulty
Medium

### Benefits for the student
The student will improve their skills in software exploitation and solvers.

### Benefits for the project
This feature would greatly help during exploits development, and people would be able to ditch mona.py for radare2 ;)

### Assess requirements for midterm/final evaluation
midterm : ROP gadgets stored in sdb, and gadget classification
final evaluation : a working ropchain builder

### Mentors
jvoisin
crowell

### Links/Resources
- [ROPGadget](http://shell-storm.org/project/ROPgadget/)
- [mona.py](https://www.corelan.be/index.php/2012/12/31/jingle-bofs-jingle-rops-sploiting-all-the-things-with-mona-v2/) from corelan
- [Hunting for ROP Gadgets in Style](https://media.blackhat.com/us-13/US-13-Quynh-OptiROP-Hunting-for-ROP-Gadgets-in-Style-WP.pdf) (2012)
- [dropper](https://github.com/rizlik/dropper) a BARF-based rop chain generator
- [Materials](http://dustri.org/b/files/hacklu2014_r2_exploitation.tar.xz) about the exloitation workshop at Hack.lu 2014
- [Slides](https://github.com/XVilka/hacklu) for the exploitation part of workshop at Hack.lu 2015 
- [ROP related bugs](https://github.com/radare/radare2/issues?q=is%3Aissue+is%3Aopen+ROP)

## Improve remote debugging with GDBServer and RAP
Having a reusable implementation of gdbserver in r2 will be useful because it means that r2 will be able to be used from IDA, GDB or LLDB as frontend. And being able to use r2 too to communicate with a remote r2 instance with better integration for remote debugging.

Also, the current r2 remote debugging is done via rap:// which is just a plain io+system protocol. it will be good to support a remote debugging via serializing r2 commands so we need a debug_rap plugin.

### Task
- Implement simple GDB packets parser for server side
- Merge/share this code with [shlr/gdb](https://github.com/radare/radare2/tree/master/shlr/gdb)
- Add support for:
  - registers access
  - memory access
  - breakpoints
  - single stepping
  - kill signal for the target
  - handling threaded applications
- Think about shareable between server and client register and platform profiles
- Implement those profiles for:
  - x86 (x86_64)
  - ARM (ARM64)
  - MIPS
  - PowerPC
  - other common architectures

### Skills
Student should know C, have some experience with socket/network programming and a general idea about how debuggers works

### Difficulty
Advanced

### Benefits for the student
### Benefits for the project
### Assess requirements for midterm/final evaluation
Midterm will be successfull if the simpe gdbserver, working via sockets will be able to talk with radare2 and gdb
Final evaluation will require gdbserver which should work at least on x86, arm, mips and powerpc platforms, able to answer radare2, gdb, lldb and IDA Pro rquests.

### Mentors
pancake

### Links/Resources
- [GDB remote protocol specification](https://sourceware.org/gdb/onlinedocs/gdb/Remote-Protocol.html)
- [GDB protocol parser](https://github.com/radare/radare2/tree/master/shlr/gdb)
- [WinDbg protocol parser](https://github.com/radare/radare2/tree/master/shlr/wind)

## Timeless debugging support
We want to add support for timeless debugging in r2. This requires to design and implement a generic API that would allow to load recorded tracing sessions from tools like rr, QIRA or r2 itself. r2 canâ€™t create tracing sessions and it should be implemented in the debugging component of our tool. We already have support for debugging snapshots, so those actions should be available as callbacks in the debugger plugins, and provide some basic commands to specify which snapshot to get or set.

### Task
1. Read/write memory at any moment in the debugging history
2. Same for registers
3. Be able to seek forward/backward in time

### Skills
Student should know C and C++ (for integration with tools like RR or Qira).
And should be familiar with the ideas of reversible debugging along with the knowledge how debuggers are working.

### Difficulty
Advanced

### Benefits for the student
### Benefits for the project

### Assess requirements for midterm/final evaluation
Midterm: design and implementation of the interface and commands to work with traces taken from QIRA and RR.
Final: Add the plugin for timeless debugging feature inside r2.

### Mentors
pancake

### Links/Resources
- [RR](http://rr-project.org/) - Record and Replay framework from Mozilla
- RR [sources](https://github.com/mozilla/rr)
- [Qira](http://qira.me/)
- Qira [sources](https://github.com/BinaryAnalysisPlatform/qira)

## Handle EXE/DLL as FAT binaries

Windows programs are like Apple's FAT binaries, they contain multiple programs inside, and r2 should be able to list and select them when loading. Also, it may be possible to extract them with rabin2 -x foo.exe.
The sub-bins inside an EXE are:
1. DOS program
2. W16 program
3. W32 program
4. MSIL program (.NET)

### Task
This task also includes adding support for .NET in RBin, to be able to list the symbols, get the entrypoint, code metadata, etc. This will require rethinking some of the commands to allow switch between parts of this FAT binary on the fly.
1. Fix current fatmach0
2. dyldcache is broken
3. PE (dos, win, .net) separation
4. Add support for iOS OTA images (see issue)

### Skills
The student should be comfortable with the C language, and be familiar with windows binaries

### Difficulty
Advanced

### Benefits for the student
The student will gain a deep understanding of Microsoft's executable formats.

### Benefits for the project
Currently, there are no up to date modern tools to deal with .Net programs in a low-level manner, when decompilers fail. With this task, we'd like to fill this gap.

### Assess requirements for midterm/final evaluation
Midterm: Support of FAT binaries (Win32 native + .NET) in RBin, basic one
Final: Also should be working with listing symbols from both parts of the binary (e.g. .NET and native code), as long as other metadata. And show this metadata in rabin2 output as well.

### Mentors
pancake

### Links/Resources
- [Bug 662](https://github.com/radare/radare2/issues/662)
- [Official .Net resources](http://www.microsoft.com/net)

## Universal assembler library
Currently, radare2 uses several assemblers, and none of them is complete. It would be awesome to have a generic assembler library for a lot of architectures.

### Task
Unify assembly syntax among all supported architectures in radare2, implement this in an external library, and make it compatible with various architectures. The library should:

- be capstone compatible
- use same syntax (att/intel/masm)
- use similar api
- reuse internal representation to allow direct instruction manipulation
- have bindings for languages (at least python/ruby/js)
- be in a separate repository, like capstone, maintained as a dependency
- support for parallel execution instructions

### Skills
The student should be comfortable with the C language and assembly. Having some knowledge of some disassembly/assembly library would be a plus.

### Difficulty
Medium

### Benefits for the student
The student will have the opportunity to see uncommon architectures, and to implement a simple-but-solid assembly language parser.

### Benefits for the project
Radare2 is currently using Capstone to disassemble several architecture, having an equivalent library to assemble would greatly simplify the maintenance and the code base.

### Assess requirements for midterm/final evaluation
Midterm will require working universal assembly library for at least 4 architectures: x86, arm, mips and avr. It could be a separate library at this point. And at the final evaluation weâ€™ll expect it integrated into the radare2 framework.

### Mentors
pancake
jvoisin

### Links/Resources
- [Capstone](http://www.capstone-engine.org/) universal disassembly library

## Improve assembly syntax
Currently, radare2 uses several assemblers, and none of them is complete. It would be awesome to have a generic assembler syntax with structures and macroses for a lot of architectures.

### Task
Unify assembly syntax among all supported architectures in radare2, implement this in an external library, and make it [fasm-compatible](http://flatassembler.net/docs.php?article=manual). This backend will perform the preprocessing assembly listings, then passing it to the frontend. It should be the one library for all available architectures.

It should support:

- Simple macro language 
```
macro <name> <args> { <body> }
```
- Preprocessor operations like â€œ>>â€, â€œIâ€, â€œ&â€, â€œ==â€, etc (should have aliases like â€œshrâ€, â€œandâ€ for fasm compatibility)
- Preprocessor conditionals â€œif/else/switchâ€
- Structures like
```
struc Unit   a,b,type
{
    .offs_l      dw a & 0xFFFF
    .cntr        db 0
    .dtype       db type
    .offs_h      dw ((b >> 16) & 0xFFFF)
    .size        = $ - .offs_l
}
Nested structures and virtual
pd    PStruct

; For accessing structure fields based on some register
virtual at edi
    edi.d PStruct
end virtual
mov        eax, [edi.d.Call]
```

### Skills
The student should be comfortable with the C language and assembly.

### Difficulty
Medium

### Benefits for the student
The student will have the opportunity to see uncommon architectures, and to implement a simple-but-solid assembly language parser.

### Benefits for the project
Having a better assembler syntax will allow r2 and its users to have a multiarch assembler with syntax as handier as the one from nasm or fasm.

### Assess requirements for midterm/final evaluation
Midterm will require working universal assembly library for at least 4 architectures: x86, arm, mips and avr. It could be a separate library at this point. And at the final evaluation weâ€™ll expect it integrated into the radare2 framework.

### Mentors
pancake
jvoisin

### Links/Resources
- https://github.com/radare/radare2/issues/4122

