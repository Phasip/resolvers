# This has been a bit unmaintained and unstable, but at the time of this commit it worked fine at least... .
# resolvers.txt
Fresh list of periodically validated public DNS resolvers.
 
```bash
$ wget https://raw.githubusercontent.com/phasip/resolvers/master/resolvers.txt
$ massdns -r resolvers.txt domains_to_resolve.txt
```
# resolvers-stable-grade-N.txt
These files contain resolvers that have been available during the last N updates.
## Why?
This is a fork from janmasarik/resolvers to add more sources for the resolvers.txt list
...
People need a list of *good* resolvers (e.g. for [massdns](https://github.com/blechschmidt/massdns)). Why spend all that traffic on refreshing a private list? Let's use and improve this one! ᕕ( ᐛ )ᕗ

## How it's done 
Validation is done using [dnsvalidator](https://github.com/vortexau/dnsvalidator/) every 12 hours using **Github Actions** that push the fresh results back to this repository. 

## Thanks
- [@vortexau](https://twitter.com/vortexau) and [@codingo_](https://twitter.com/codingo_) for creating [dnsvalidator](https://github.com/vortexau/dnsvalidator)!
- GitHub for *hosting* this on GitHub Actions! :heart:
