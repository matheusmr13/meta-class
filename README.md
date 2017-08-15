# meta-class
A MetaClass that helps you to generate some JavaScript Class definitions.

## Why
I wanted to recreate [Google App Script](https://developers.google.com/apps-script/) API with [this repo](https://github.com/matheusmr13/app-script-api) without needing to look into GAS documentation. More information, visit the repo and check out (:

## Usage

Your simple code

```javascript
  const myMetaClass = new MetaClass('User', {
    properties: [
      new Propertie('name', { type: 'String' }),
      new Propertie('age', { type: 'Integer', default: 20, lookUps: true }),
    ],
    functions: [
      new Function('isUserUnderAge', { type: 'Boolean' }),
      new Function('toString', { type: 'String' }),
      new Function('createUser', { type: 'User', static: true, parameters: [ new Propertie('user', { type: 'User' }) ] } ),
      new Function('addRole', { parameters: [ new Propertie('role', { type: 'Role' }) ] } )
    ]
  });
  
  console.log(myMetaClass.build());
```

Results:

```javascript
  import Role from 'Role';
  
  class User {
    name: string;
    age: integer = 20;
    
    /* Class actions */
    static createUser(user: User ): User {
      // TODO implement
    }
    
    /* Instance actions */
    addRole(role:  Role) {
      // TODO implement
    }
    
    toString(): string {
      // TODO implement
    }

    /* Look ups */
    get age() {
      // TODO implement
    }
    
    set age() {
      // TODO implement
    }
  }
  
  exports default User;
```

## Next features
- [ ] Choose between ES6 / ES5 / Before
- [ ] Private properties and which approach
- [ ] Specify path to dependencies
- [ ] Choose with static typer (flow / Typescript / None)
- [ ] Specify .eslint file to generate following rules
