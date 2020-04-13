# what-i-learned-in-week-12


![swotty.dev logo](assets/swotty-dot-dev-logo.svg.png)

## Contents
* Objects and its functions
* classes, constructor function, super(), default parameters in function 
* anonymous function  
  
### Objects and its functions

Objects in javascript is an entity with properties and can include functions.

below is an examples of how to declare an object and how to use properties with dot
notation and bracket notation.

```
const myObj = {} // this is an empty object

//another example with prepopulated key:value data (Object Literal)

const myObjPrepopulated = {
    firstName: 'Bogdan',
    catName: 'Tesla'
}

//example of dot notation to add new key:value pair
myObj.name = 'Bogdan'

//example with bracket notation
myObj['CatName'] = Tesla //please note it is useful if you have a special string to be used as key

// example of function as value in a key

const myObjWithCustomFunctionsSlashMethods = {
    firstName: 'Bogdan',
    lastName: 'Kowaltchook',

    getFullName: function() {
        return `${this.firstName} ${this.lastName}/*Please Note that keyword 'this' in the case refers to its own object's property.
    }
}
```
  

### Classes, constructor function, super()

Clases are special objects that can be declared and used in inheritance for other classes and its functions. We have been introduced to OOP (Object Oriented Programming). Classes seem to be an object with constructor function that creates an object using 'this' keyword and various other function within the original class that can be called with 'super()' function . Classes that inherit parent functions and properties use 'extends' keyword.

below are code examples

```
//declaration of main class with constructor (creates an object for us). We are also introduced in this example to default parameter values in a function, hence if no parameter is passed then default value will be passed.

class microphone {
    constructor(type = electret,/*this is default which is electret in parameter if nothing is passed*/ name, directivity) {
    this.type = type;
    this.name = name;
    this.directivity = directivity;
    }

    fullParameters() {
        return `Type:${this.type}, Name:${this.name}, Directivity:${this.directivity} 
    }
}

class BlueYetiMic extends microphone {
    constructor(directivity) {
        super('condeser', 'BlueYeti', directivity)
    }
}

```

### Anonymous functions

Anonomous functions are functions that are not declared (no name needed I mean) and usually are written inside of another function to be used in its parent function. We covered functions that could be used with conjunction of object/arrays methods such as '.map' , '.filter' , '.sort'

below is a example of one such functions:

```
//Prelimenary helper function to create an object:

const makeDino = function(species, period, carnivore, extinct = false) {
    const dino = {
    species: species,
    period: period,
    carnivore: carnivore,
    extinct: extinct,
    }
    return dino;
}


//function with anonymous function:

const truncateDions = function(dinos) {
    const copyOfDinos = [...dinos];
    return dinos.map(function(dino) { /*this is where our anonymous function resides*/
        const copyOfDinoInternal = makeDino(dino.species, dino.period, dino.carnivore, dino.extinct);

        if(copyOfDinoInternal.species.length > 10) {
            copyOfDinoInternal.species = `${copyofDinoInternal.species.substr(0, 7)}...`;
        }
        return copyOfDinoInternal;
    });

}

```