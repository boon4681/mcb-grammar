# Wrapper

Wrapper class is a class designed to return compiled code as a String when the compiler or operator do actions with it.

The differences of wrapper function and builder function

1. Wrapper class are based on "inheritance concept" that mean variables inside can share to children function except game variables. game variables are not allowed to share their value with builder function.
2. Wrapper class can override operators.
3. Wrapper class can stack builder function.

```ts
#[Wrapper]
class Name<wrapper_param,...>{
    fun Name(){
        // ..code..
    }

    #[builder]
    fun Name(){
        // ..code..
    }
}

```

```ts
#[Wrapper]
class score<criteria:String>{

    #[builder]
    fun _score_(){
        > f'scoreboard objective add ${this.name} ${this.criteria}'
    }

    #[builder]
    fun remove(){
        > f'scoreboard objective remove ${this.name}'
    }

    #[builder]
    fun _selector_assign_(selector:String|Entity,by:Int32){
        > f'scoreboard objective set ${this.name} ${selector} ${by}'
    }

    #[builder]
    fun _selector_assign_(selector:String|Entity,by:int){
        > f'scoreboard objective operation ${this.name} ${selector} = ${by.scoreboard.name} ${by.target}'
    }
}
```

```ts
#[Wrapper]
class int<scoreboard:score>{

    struct {
        target: String
    }

    #[builder]
    fun _int_(){
        this.declaration_builder(this.name,'0')
    }

    #[builder]
    fun _int_(default_value:Int32){
        this.declaration_builder(this.name,default_value)
    }

    #[builder]
    fun _int_(as_target:String|Entity){
        this.declaration_builder(as_target,'0')
    }

    #[builder]
    fun _int_(default_value:Int32,as_target:String|Entity){
        this.declaration_builder(as_target,default_value)
    }

    #[builder]
    fun declaration_builder(name:String,value:Int32){
        this.target = name
        > f'scoreboard players set ${name} ${this.scoreboard.name} ${value}'
    }

    #[builder]
    fun operation_builder(to:This,by:This,operator:String){
        > f'scoreboard players operation ${to.target} ${to.scoreboard.name} ${operator}= ${by.target} ${by.scoreboard.name}'
    }

    #[builder]
    fun operation_builder(to:This,by:Int32,operator:String){
        let name = utils.mcb_scoreboard_target(to.scoreboard.name,true)
        > f'scoreboard players set ${name} ${to.scoreboard.name} ${by}'
        > f'scoreboard players operation ${to.target} ${to.scoreboard.name} ${operator}= ${name} ${by.scoreboard.name}'
    }

    // Int32 operation

    #[builder]
    fun _add_(by:Int32){
        this.operation_builder(this,by,'+')
    }

    #[builder]
    fun _sub_(by:Int32){
        this.operation_builder(this,by,'-')
    }

    #[builder]
    fun _div_(by:Int32){
        this.operation_builder(this,by,'/')
    }

    #[builder]
    fun _mult_(by:Int32){
        this.operation_builder(this,by,'*')
    }

    // int operation

    #[builder]
    fun _add_(by:This){
        this.operation_builder(this,by,'+')
    }

    #[builder]
    fun _sub_(by:This){
        this.operation_builder(this,by,'-')
    }

    #[builder]
    fun _div_(by:This){
        this.operation_builder(this,by,'/')
    }

    #[builder]
    fun _mult_(by:This){
        this.operation_builder(this,by,'*')
    }
}
```
