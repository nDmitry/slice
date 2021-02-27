# slice

Package `slice` implements some popular helpers for working with Go slices in functional manner.

It uses Go generic syntax according to the [proposal](https://go.googlesource.com/proposal/+/refs/heads/master/design/go2draft-type-parameters.md) that might be implemented in the language in Go 1.18.

## Usage

```go
package main

import "github.com/nDmitry/slice"

func main() {
    ints := []int{1, 2, 3, 4, 5}
    strings := []string{"eat", "a", "cake"}

    fmt.Println(
        slice.Filter(ints, func(item int, _ int) bool { return item%2 == 0 }),
        slice.Filter(ints, func(item int, i int) bool { return i%2 == 0 }),
        slice.Filter(strings, func(item string, _ int) bool { return len(item) == 4 }),

        slice.Some(ints, func(item int, _ int) bool { return item%2 == 0 }),
        slice.Every(ints, func(item int, _ int) bool { return item%2 == 0 }),

        slice.Find(ints, func(item int, _ int) bool { return item%2 == 0 }),
        slice.FindLast(ints, func(item int, _ int) bool { return item%2 == 0 }),
        slice.FindIndex(ints, func(item int, _ int) bool { return item%2 == 0 }),
        slice.FindLastIndex(ints, func(item int, _ int) bool { return item%2 == 0 }),

        slice.Map(ints, func(item int, _ int) int { return item * item }),
        slice.Map(ints, func(item int, _ int) float64 { return float64(item) * 0.5 }),

        slice.Reduce(ints, func(sum int, item int, _ int) int { return sum + item }, 0),
    )
}
```
