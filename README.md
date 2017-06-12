# Gexec

Gexec originates from [oklog](https://github.com/oklog/oklog/tree/master/pkg/group)
where it was originally made and designed by [Peter Bourgon](https://github.com/peterbourgon).
The library was extracted so that it can be used as an independent library
without having to bring in more dependencies than required.

At some point additions have been made, but the core has remained the same.

## Examples

For more detailed examples [see](/example_test.go)

```go
var g gexec.Group
{
    listener, := net.Listen("tcp", ":0")
    g.Add(func() error {
        return http.Serve(listener, http.NewServeMux())
    }, func(err error) {
        listener.Close()
    })
}
// Execute the group
fmt.Println(g.Run())
```
