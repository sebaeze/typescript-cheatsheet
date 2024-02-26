#  Typescript Cheatsheet

## Property modifier

- readonly: Makes a property read-only within the class, object, interface or type.

## Utilities

### Generics

- Partial: Convert all the properties to optional.
```ts
interface IRepository {
    title: string;
    language: string;
}
// let myRepositoryA:IRepository = {} ; <--- TS ERROR
let myRepositoryB:IRepository = {} as IRepository ; // <--- works
let myRepositoryC:Partial<IRepository> = {} ;       // <--- Using Partial utility
//
```

- Readonly: Makes all the properties read-only
```ts
let myArray:Readonly<string[]> = ['valueA','valueB'];
myArray.push( 'valueC' ) ; // <--- Error
``` 

- 

## Decorator

### Basic decorator
```ts
function Logger(myClass: Function){
    console.log("...myClass: ",myClass) ;
}

@Logger
class TestClass{
    constructor(private myProperty:string){}
    getMyProperty(){
        return this.myProperty;
    }
}
```

### Decorator factory

```ts
function ImprovedLogger(loggerName: string){
    return function (myClass: Function){
        console.log( new Date().toISOString()+`_${loggerName}::myClas: `,myClass) ;
    }
}
@ImprovedLogger('logging_decorator_TestClass')
class TestClass{
    constructor(private myProperty:string){}
    getMyProperty(){
        return this.myProperty;
    }
}
/*  */
let newClass = new TestClass("propertyFake") ;
console.log("....newClass: ",newClass,";") ;
/*  */
```

### Multiple decorators



