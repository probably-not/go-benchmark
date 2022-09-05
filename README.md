# Golang benchmarks

Forked this from the original project and decided to run it to test out if valyala's Bytesbufferpool is still actually the fastest according to what they say...

Surprisingly, in the latest Go releases, they're much much slower than the others in the pure benchmark.
The clear winner is the standard library sync.Pool wrapping a bytes.Buffer.

## Results

```
goos: darwin
goarch: arm64
pkg: github.com/probably-not/go-benchmark/buffer/main
BenchmarkGenericBuf-10                           3144300               396.2 ns/op          1536 B/op          4 allocs/op
BenchmarkGenericStackBuf-10                      2913848               393.9 ns/op          1536 B/op          4 allocs/op
BenchmarkAllocBuf-10                             2992111               389.4 ns/op          1536 B/op          4 allocs/op
BenchmarkSyncPoolBuf-10                         123326943                9.478 ns/op           0 B/op          0 allocs/op
BenchmarkBpoolPoolBuf-10                         9340093               145.0 ns/op             0 B/op          0 allocs/op
BenchmarkByteBufferPoolBuf-10                   14185982                85.92 ns/op            0 B/op          0 allocs/op
BenchmarkEasyJsonBuffer-10                       6211806               234.7 ns/op           600 B/op          4 allocs/op
BenchmarkEasyJsonBuffer_OptimizedConfig-10      66843327                21.81 ns/op           24 B/op          1 allocs/op
```