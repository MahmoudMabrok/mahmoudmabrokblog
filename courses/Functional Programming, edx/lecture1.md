- # Part 1        
    ### Functional 
    - is based on lambda calculs.
    - functional programming
                is a style of programming in which
                **expressions** are more **important** than using **statements**.
    - When you compose **statements** the statements have an **implicit side-effect**
                on the global state and they communicate values via that global
                state.

    ### example for non-functioal 
    here example of sum of integers.
  ``` java 
        int total =0 ; 

        for (int i =0 ; i < 10 ; i ++ ){
            total += i ; 
        }
     ``` 
    that is example of **imperative style** in which 
        - we declare varible ` total `
        - iterate through loop with loop varible `i`
        - use mutable states `total`

    # functioal-style

    ``` haskell
        sum [1..10]
    ```
     - based on expression rather than statements.
     - `[1..10]` is expression to create list 


- # part2
    - some histrocal data 
        - **Lisp** impertive + functional programming.   
        - **ISWIM** first pure functional programming.
        - **Haskell** pure functional programming  

