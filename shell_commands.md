## Load every environment variable from file
`source <(cat development.env | sed -e '/^#/d;/^\s*$/d' -e "s/'/'\\\''/g" -e "s/=\(.*\)/='\1'/g")`
**Explanation:**
1. `/^#/d` removes comments (strings that start with #)
2. `/^\s*$/d` removes empty strings, including whitespace
3. `"s/'/'\\\''/g"` replaces every single quote with '\'', which is a trick sequence in bash to produce a quote :)
4. `"s/=\(.*\)/='\1'/g"` converts every a=b into a='b'

## Add path to $PATH environment variable
`export PATH="NEW_PATH:$PATH"`
