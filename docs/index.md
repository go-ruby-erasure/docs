# go-ruby-erasure

Pure-Go core of the Ruby `erasure` gem (Reed-Solomon + Mojette).

`go-ruby-erasure` is the pure-Go, Ruby-runtime-independent core of the Ruby `erasure` gem: a reflective adapter over [`go-erasure/reedsolomon`](https://github.com/go-erasure/reedsolomon) and [`go-erasure/mojette`](https://github.com/go-erasure/mojette), shaped so the [go-embedded-ruby](https://github.com/go-embedded-ruby) interpreter can bind it as `require "erasure"`. It is equally usable as a standalone Go library.


!!! note
    The rbgo `require "erasure"` binding that wires this adapter into the Ruby interpreter lives in [go-embedded-ruby](https://github.com/go-embedded-ruby), not in this org.

## Repositories

<div class="repo-grid" markdown>
<a class="repo-card" href="repos/erasure.md"><code>erasure</code><br><small>Reflective adapter over go-erasure/reedsolomon and go-erasure/mojette, returning Ruby-shaped values.</small></a>
</div>
