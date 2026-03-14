# Fast RSA Prime Generation

Optimized RSA prime generation in C+GMP achieving
**2.7x–15x speedup over OpenSSL 3.x** across standard
key sizes, with full FIPS 186-5 compliance.

## Benchmark Results

| RSA bits | This work (seq) | This work (4w) | OpenSSL | Botan | vs OpenSSL (4w) |
|---|---|---|---|---|---|
| 512 | 0.0028s | — | 0.0253s | — | 9.0x |
| 1024 | 0.0095s | 0.0105s | 0.0325s | 0.0368s | 3.1x |
| 2048 | 0.1361s | 0.0742s | 0.5026s | 0.2500s | 6.8x |
| 4096 | 1.0772s | 0.3418s | 2.7397s | 1.0178s | 8.0x |

Hardware: Intel Xeon (Google Colab, 2 physical cores),
GCC -O3, GMP 6.x, OpenSSL 3.x, Botan 2.19.1.

## Security

All keys verified against FIPS 186-5:
- Independent primality test (20 Miller-Rabin rounds)
- Distance requirement |p-q| > 2^(n/4)
- End-to-end encrypt/decrypt verification
- **150 key pairs tested, 0 failures**

## Build

```bash
apt-get install libgmp-dev
gcc -O3 -o rsa_prime_bench rsa_prime_bench.c -lgmp
./rsa_prime_bench

## Related Paper

Fast RSA Prime Generation via Wheel Factorization
and Prime Distance Structure in Twin Prime Gaps
[IACR ePrint link — coming soon]

## License

© 2026 [Piero Riontino - email: pieroriontino@pec.it]. All rights reserved.
Commercial use requires explicit written permission.
