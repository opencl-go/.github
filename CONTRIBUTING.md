## Contributing Guidelines

Thank you for considering to contribute to this project!

The following text lists guidelines for contributions.
These guidelines don't have legal status, so use them as a reference and common sense - and feel free to update them as well!

### "I just want to know..."

The wrapper libraries of this project are just that: wrappers to the existing API.
For questions or general information about **OpenCL** itself, it may be better to refer to otherwise available sources, such as books about OpenCL, [StackOverflow][stackoverflow], or the extensive documentation of [Khronos Group][khronos].
Still, if you want to focus on this project here, please use the [discussion board][opencl-go-discussions] instead of creating an issue.

[stackoverflow]: https://stackoverflow.com/questions/tagged/opencl
[khronos]: https://www.khronos.org/opencl/
[opencl-go-discussions]: https://github.com/opencl-go/opencl-go.github.io/discussions

### Scope

The wrappers of this project intend to provide the functionality of the **OpenCL** API in their respective versions, and expose them in a "Go idiomatic" way.

#### What is idiomatic
While the definition of what is "idiomatic" may change over time and be different between people, there are some common, well-known common guides on the page on "[Effective Go][effective-go]".

> Most notably, the 'getter' functions in Go do not have `Get` as a prefix. Which is why it is called `cl.PlatformIDs()` and not `cl.GetPlatformIDs()`.

[effective-go]: https://go.dev/doc/effective_go

### Extensions
If you can and want to make use of this library in your own projects, you are happy to do so.
Pull-requests with extensions are happily accepted, provided that they uphold the following minimum requirements:

* Code is properly formatted & linted (use [golangci-lint](https://github.com/golangci/golangci-lint) for a full check)
* Public Go API is documented. Make use of the CreativeCommons licensed asciidoctor documentation from [OpenCL Docs][opencl-docs]. In any case, please make the comments readable as complete English sentences, as recommended by Go.
* Any new functionality is covered in all the current wrappers where it is missing. This affects OpenCL extensions especially.

[opencl-docs]: https://github.com/KhronosGroup/OpenCL-Docs

### Code Style

Please make sure Go code is formatted according to `go fmt`, and use the following linter: [golangci-lint](https://github.com/golangci/golangci-lint).

> If there are linter errors that you didn't introduce, you don't have to clean them up - They might have been missed previously and hopefully will be handled separately. However, fixing them proactively gives you bonus points :)

#### Handling of deprecated functions

In case a function, constant, or otherwise exported element is considered deprecated as per OpenCL spec, mark it as such in the wrappers of the deprecating and earlier versions:

```
// OldFunction does something.
// Deprecated: 2.2
func OldFunction() {
    ...
}
```

Things that should no longer be present in later versions should also not be provided by the corresponding future version wrappers.

