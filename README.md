clang-restructure
=================
The goal of this project is to create a highly configurable tool to deal with legacy code bases,
based on the CLang libraries and toolset.

Dealing with old code you come across any number of problems including but not limited to
-   100 lines of includes on top of a 20000 line implementation file, where nobody really knows why
    any of those includes is there
-   Header files including unnecessary files
-   Header files requiring other files to be included before
-   Use of includes instead of forward declarations
-   Classes are declared in headers where you don't expect them to be
-   A complete mess of 2000 lines of intermixed class declarations, inline function declarations and
    maybe some unused forward declarations to flavor the mix

Features
--------
We are planning to implement following features
-   Parsing a complete project and all dependencies to build an abstract representation of the
    dependencies of the all components used in the project.
-   Cycle detection and possibly semiautomatic resolution.
-   Customizeable cleanup of includes, supporting #define based multiple include of a single header
    file to support working with external c header files that cannot be changed.
-   Detection of includes that can safely be replaced by forward declarations.
-   Making a header file self-contained by adding / changing #include directives.
-   Restructuring of namespaces and classes into header files with highly customizeable naming
    conventions, with optionally rewriting the #include directives in all affected translation
    units.
-   Refactoring header files dependent on #defines into multiple independent files while rewriting
    the include directives in all affected translation units.
-   Automatic generation of end-user compatible migration instructions
-   Automatic generation of legacy header files, representing the state before the conversion was
    done.
-   Splitting translation units based on user-defined rules.

Special points to consider
--------------------------
 -  Operators
 -  Magic comments to control the tool's behaviour
 -  Unusual use of header files
 -  Macro definitions
 -  extern "C"

Links
-----
-   https://github.com/BentleyJOakes/PCX
