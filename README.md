### Problem:
I was a bit confused how long the compilation took and how much RAM was required, when playing aorund with the develop branch when using the nativ Sha256 libraries. Having done quite a bit of hashing with ZoKrates, it seemed off. Initially I thought this would be a problem with the develop branch, however the same behaviour is found on master.

In `zkRelay_val.zok` we do 18 rounds of sha256 hashing, `validate_block_header()` is called 3x: for the 1024bit hash 4 rounds, for the 256bit hash 2 rounds => Total 18 rounds.

However, when compiling `512bitx10.zok` (which does 20 sha256 rounds) compilation takes almost 9x as long, and ram usage is up x6.5. While `zkRelay_val.zok` does contain some other logic, this is very surprising and doesn't really make sense to me. The file is also a bit messy, but I think it will suffice for an example

### Results:
|file             |compile_opt_microsec|memusg_compile_KiB|constraints|
|-----------------|--------------------|------------------|-----------|
|512Bitx10Embed   | 2534824            | 444032           | 277802    |
|512bitx10        | 410881180          | 26738596         | 363184    |
|512bitx10_no_loop| 413493618          | 26738504         | 363184    |
|zkRelay_val      | 48289868           | 4066328          | 292357    |
|getHexLength     | 882580             | 39560            | 22612     |

These results come from a server with 60GB ram, locally this will run a lot slower. 

