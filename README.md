# Base32Crockford

This is a minor fork to support Elixir 1.18 and above.  I do not plan
to publish this on hex.pm.

Original README (with changes to URLs, etc.):

An alternate base32 encoding as described by Douglas Crockford at: 
[https://www.crockford.com/wrmg/base32.html](https://www.crockford.com/wrmg/base32.html)

It is used for expressing integer numbers in a form that can be conveniently 
and accurately transmitted between humans and computer systems.

The encoding is designed to:

- Be human and machine readable
- Be compact
- Be error resistant
- Be pronounceable

A symbol set of 10 digits and 22 letters is used:
`0123456789ABCDEFGHJKMNPQRSTVWXYL`
It does not include 4 of the 26 letters: I L O U.

A check symbol can be appended to a symbol string. 5 additional symbols
`*~$=U` are used only for encoding or decoding the check symbol.

When decoding, upper and lower case letters are accepted,
and `i` and `l` will be treated as `1` and `o` will be treated as `0`.
When encoding, only upper case letters are used.

## Installation

The package can be installed as:

  1. Add base32_crockford to your list of dependencies in `mix.exs`:

    ```elixir
    def deps do
      [{:base32_crockford, git: "https://github.com/faried/base32_crockford.git", branch: "master"}]
    end
    ```

  2. Run `mix deps.get` in your console to fetch from Hex


## Usage

```elixir
iex> Base32Crockford.encode(1_000_000_000)
"XSNJG0"

iex> Base32Crockford.encode(1_000_000_000, partitions: 2)
"XSN-JG0"

iex> Base32Crockford.decode("XSNJG0")
{:ok, 1000000000}

iex> Base32Crockford.decode!("XSNJG0")
1000000000
```
    
## Documentation
Hosted on [http://hexdocs.pm/base32_crockford/readme.html](http://hexdocs.pm/base32_crockford/readme.html)

## Author
Vladimir Zhukov
Faried Nawaz

Base32Crockford is released under the [MIT License](https://github.com/faried/base32_crockford/blob/master/LICENSE).
