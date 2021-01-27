### Problem:
With the new develop branch, compilation of the nativ sha256 libraries breaks for me. I haven't seen the compilation terminate until now, on a server with 60GB ram errors where thrown because the server was running out of ram. This is new behaviour, the libraries in the latest release work as expected. Interestingly, this only seems to happen with a larger number of hashes. If there in a for loop or not, doesn't seem to make a difference.

### Steps


### Results:
- sha256Embedx10.zok compiles in ~20 sec
- sha256x10.zok doesn't terminate after ~3m and unsing 5.8GB ram, 7GB after 5m, 8GB after 7m
- sha256x10_no_loop.zok nop termination, ~7.4GB ram after 4m