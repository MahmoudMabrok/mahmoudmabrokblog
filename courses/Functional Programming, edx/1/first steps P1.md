# Basics of Haskell 

- ``` head [1, 2,3 ,4 , 5 ] ``` ==> first element on list
- ``` tail [1, 2,3 ,4 , 5 ] ``` ==> last element on list
- ``` take 3 [1, 2,3 ,4 , 5 ] ``` ==> return first 3 items element on list
- ``` drop 3 [1, 2,3 ,4 , 5 ] ``` ==>  remove first  3 items element on list
- ``` length [1, 2,3 ,4 , 5 ] ``` ==> count of elements of a list
- ``` sum [1, 2,3 ,4 , 5 ] ``` ==> sum  element on list


- calling the function **length**. Length of [1,2,3,4,5] is 5. Again, lists in Haskell are **not like arrays**
in other languages, so taking the **length** is **not a constant time operation.**

## Function 
- in physics function represented by `f(a,b) + c d` 
  - explicity specify argument by using parenthesis`()`.
  - **multiplication** is specified by space `c d`.

- in **Haskell**
 `f a b + c*d`
   - function is specified by **only white space**.
   - function is **higher priority** so `f a + c ` is function of a then added  with c.
   - **multiplication** is specified by space `c*d`.


## Examples 

Mathmatics Rep.    |  Haskell Rep.
----     |  -------
f(x,y) | f x y
f(g(x)) | f (g x)
f(x , g(y)) | f x (g y)









