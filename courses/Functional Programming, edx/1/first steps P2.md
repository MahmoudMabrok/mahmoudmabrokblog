- is prefered to say for code as **script** rather than **program** 
- suffix is ``.hs``


# First script 

- Open a new file named `test.hs`
``` haskell 
double x = x + x

quadruple x  = double (double x)

```
- open ghci with script using `ghci test.hs`.
- write script 
```
take (double 2 ) [1..10]
Output -> [ 1 2 3 4 ]
```

# continue 
add two functions to `test.hs`
```
factorial x = product [1..x]

average ns = sum ns `div` length ns
```

- here are back single quote which convert **div** into **infix** for ``example`` 
  -   ``` x `f` y ``` is equivalent to ```f x y```.


# Naming Conventions 
- *functions, arguments* must **start** with **lower caase**.
- *list argument* has **suffix** `s` for ex:
  - ``ns`` list of n  , ``xs`` list of x  , `nss` here it refer to list of list.



# Layout Rule
all with same column.

# useful GHCI Commands 

Command | Means
------ | ------ 
reload | reload current script
load scriptName | load script file  
? | show al commands
type expr | type expression 

