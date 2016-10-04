# boost.filesystem

The **Boost.Filesystem** library provides facilities to manipulate files and directories, and the paths that identify them.

## Features

The features of the library include:

* A modern C++ interface, highly compatible with the C++ standard library.

  > Many users say the interface is their primary motivation for using Boost.Filesystem. They like its use of familiar idioms based on standard library containers, iterators, and algorithms. They like having errors reported by throwing exceptions.

* Portability between operating systems.
 
  > At the C++ syntax level, it is convenient to learn and use one interface regardless of the operating system.
  > At the semantic level, behavior of code is reasonably portable across operating systems.
  > Dual generic or native path format support encourages program portability, yet still allows communication with users in system specific formats.
 
* Error handling and reporting via C++ exceptions (the default) or error codes.
 
  > C++ exceptions are the preferred error reporting mechanism for most applications. The exception thrown includes the detailed error code information important for diagnosing the exact cause of file system errors.
  > Error reporting via error code allows user code that provides detailed error recovery to avoid becoming so littered with try-catch blocks as to be unmaintainable. 
 
* Suitable for a broad spectrum of applications, ranging from simple script-like operations to extremely complex production code.
 
  > At the simple script-like end of the spectrum, the intent is not to compete with Python, Perl, or shell languages, but rather to provide filesystem operations when C++ is already the language of choice.
  > Finer grained control over operations and error handling is available to support more complex applications or other cases where throwing exceptions isn't desired.

* Forms the basis for ISO/IEC TS 18822, the C++ standard library Filesystem Technical Specification.

## Boost Dependencies

[Boost.Align](https://github.com/boostorg/align)
[Boost.Array](https://github.com/boostorg/array)
[Boost.Assert](https://github.com/boostorg/assert)
[Boost.Bind](https://github.com/boostorg/bind)
[Boost.ConceptCheck](https://github.com/boostorg/concept_check)
[Boost.Config](https://github.com/boostorg/config)
[Boost.Core](https://github.com/boostorg/core)
[Boost.Detail](https://github.com/boostorg/detail)
[Boost.Function](https://github.com/boostorg/function)
[Boost.FunctionTypes](https://github.com/boostorg/function_types)
[Boost.Functional](https://github.com/boostorg/functional)
[Boost.Fusion](https://github.com/boostorg/fusion)
[Boost.Integer](https://github.com/boostorg/integer)
[Boost.IO](https://github.com/boostorg/io)
[Boost.Iterator](https://github.com/boostorg/iterator)
[Boost.Move](https://github.com/boostorg/move)
[Boost.MPL](https://github.com/boostorg/mpl)
[Boost.Numeric.Conversion](https://github.com/boostorg/numeric_conversion)
[Boost.Optional](https://github.com/boostorg/optional)
[Boost.Predef](https://github.com/boostorg/predef)
[Boost.Preprocessor](https://github.com/boostorg/preprocessor)
[Boost.Range](https://github.com/boostorg/range)
[Boost.Regex](https://github.com/boostorg/regex)
[Boost.SmartPtr](https://github.com/boostorg/smart_ptr)
[Boost.StaticAssert](https://github.com/boostorg/static_assert)
[Boost.System](https://github.com/boostorg/system)
[Boost.ThrowException](https://github.com/boostorg/throw_exception)
[Boost.Tuple](https://github.com/boostorg/tuple)
[Boost.TypeIndex](https://github.com/boostorg/type_index)
[Boost.TypeTraits](https://github.com/boostorg/type_traits)
[Boost.Typeof](https://github.com/boostorg/typeof)
[Boost.Utility](https://github.com/boostorg/utility)
