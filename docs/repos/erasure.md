# erasure

Reflective adapter over go-erasure/reedsolomon and go-erasure/mojette, returning Ruby-shaped values.

A `Session` exposes Reed-Solomon (`EncodeRS`/`VerifyRS`/`ReconstructRS`) and Mojette (`EncodeMojette`/`ReconstructMojette`/`Reconstructible`) as typed methods, plus `Call(ctx, method, args...)` that routes a snake_case name to the matching operation, coercing Ruby-decoded arguments and returning Ruby-shaped values.

## Highlights

- Wraps both erasure codecs behind one Ruby-shaped surface.
- Ruby data shapes: shards as byte strings, shard sets as `Array`, present mask as `Array` of booleans, projections as `Hash {"p","q","bins"}`.
- `Call` reflective dispatch drives `method_missing`; unknown methods or argument mismatches return a clear error.
- `CGO_ENABLED=0`, no dependency on the Ruby runtime; builds for all nine 64-bit targets.

## Example

```go
s := erasure.NewSession()
full, _ := s.EncodeRS(2, 2, dataShards)              // []any data+parity
ok,   _ := s.VerifyRS(2, 2, full)                    // bool
rec,  _ := s.ReconstructRS(2, 2, damaged, present)   // recovered set
projs, _ := s.EncodeMojette(2, 2, 2, gridBlocks, dirs)
grid,  _ := s.ReconstructMojette(2, 2, 2, projs)
```

## Install

```sh
go get github.com/go-ruby-erasure/erasure
```

Requires Go 1.26 or newer.

## Links

- Source — <https://github.com/go-ruby-erasure/erasure>
- API reference — <https://pkg.go.dev/github.com/go-ruby-erasure/erasure>

!!! note
    The rbgo `require "erasure"` binding that wires this adapter into the Ruby interpreter lives in [go-embedded-ruby](https://github.com/go-embedded-ruby), not in this org.
