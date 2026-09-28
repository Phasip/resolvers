# resolvers.txt
Fresh list of periodically validated public DNS resolvers (IPv4, one per line).

```bash
$ wget https://raw.githubusercontent.com/phasip/resolvers/master/resolvers.txt
$ massdns -r resolvers.txt domains_to_resolve.txt
```

# resolvers-stable-gradeN.txt
`resolvers-stable-grade1.txt` … `resolvers-stable-grade11.txt` contain resolvers that passed validation in
at least the last N+1 consecutive runs (grade1 = this run and the previous one, grade11 = the last 12 runs,
i.e. about 6 days). Each grade is a subset of the grade below it, so a higher grade trades size for stability.

## Why?
This is a fork of [janmasarik/resolvers](https://github.com/janmasarik/resolvers) that adds more sources for the resolvers.txt list.

People need a list of *good* resolvers (e.g. for [massdns](https://github.com/blechschmidt/massdns)). Why spend all that traffic on refreshing a private list? Let's use and improve this one! ᕕ( ᐛ )ᕗ

## How it's done
Every 12 hours a **GitHub Actions** workflow ([`.github/workflows/main.yml`](.github/workflows/main.yml)):

1. Takes the resolvers from the current `resolvers.txt` first, then fills up to 2500 candidates with new ones from
   [public-dns.info](https://public-dns.info/nameservers.txt) and the
   [massdns resolver list](https://github.com/blechschmidt/massdns/blob/master/lists/resolvers.txt).
2. Validates them with [dnsvalidator](https://github.com/vortexau/dnsvalidator/).
3. Updates the grade files and pushes the result back to this repository.

## Thanks
- [@vortexau](https://twitter.com/vortexau) and [@codingo_](https://twitter.com/codingo_) for creating [dnsvalidator](https://github.com/vortexau/dnsvalidator)!
- GitHub for *hosting* this on GitHub Actions! :heart:
