

# using type alias 
Used normally to give a new name for existing type or construct a new type.
`type ContactAddress = string` it is actual string type but has different name. 
other useful uses can be: 
- `type ContactAddress = string | Date`: says it can be one type of string, Data. 
- `type ContactAddress = Contact & Address`: combine two types into one type. 
- `type status = 'active' | 'inactive'`: can be used like enum to define restricted values. 
    - Note: we can use `|` directly like `function print(a: string | number)` 

# typeof 
- used to retrive type of object/field like ` if (typeof contact.birthDate === "number")`
- can be used to define a new type without need an interface:
    ``` typescript
        const user = {name:"mahmoud" , age:15}; 
        function printUser(params: typeof user) {
            
        }
        // note: typeof can not be used with type like User, Contact it needs actual object/value.

    ```
# keyof
retrive properties/keys as union like `type title = keyof User` so it can be used later with something like indexed access types. 

# indexed access types
Get type by access property like: 
``` typescript
{
 contactId: Contact["id"]; 
}
```
`contactId` here will be of type same as property "id" of `Contact`.


# using Record 
- Record used to define a type with dynamic values and types. 
- It need possible property **values** & possible property **types**. 
- Let's have a sample


# Modules 
- In JS we can use modules to organize our code and export what we need then import it where needed. 
    - for exporting 
        ```js
        // let say file name is util.js
        export function doSomeThing(){

        }
        ```

    - for importing 
        ```js
        // let say file name is app.js
        import { doSomeThing } from "./util.js"

        doSomeThing(); 
        ```
    - when use it in browser we will need only reference `app.js`:
        ```js 
        <script type="module"  src="app.js"></script>
        ```

- you can define `global.d.ts` to define methods you want to export between modules and get support of typescript [this only make definition for exported methods]
    - code 

    ```typescript 
    declare global {
        // that doSomeThing
        function dodoSomeThing():string 

    } 

    export {} 

    ```

    - this will not make code avaiable at runtime of web page, you will need to **add** both files.  

## Declaration merging 
- It is a feature that allow you to add more methods and property to existing classes or external classes. 
- Steps
    - just declar interface with same name and define inside it what you need 
    ```ts 
        class Customer{

        }

        interface Customer {
            save():void
        }

        const customer = new Customer();
        customer.save = function(){
            // do what yuo want
        }        

    ```   
    - here ts jsut **merge** two declarions. 
- can be used to add **property** to **window** object which we do not own, this can be done by having `global.d.ts` that have interface with name `Window` then add what you want.     
    ```typescript 
    declare global {
        
        interface Window {
            // value of something
            myValue:string 
        }

    } 

    export {} 

    ```

## Running it 
- to use exports with ts you will need to add `"module": "CommonJS"` to `compilerOptions` this for node application

- for web app you will need to use bundle apps like `webpack`, `parcel`.
