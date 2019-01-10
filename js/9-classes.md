# Classes
```js
class Car {
    constructor(doors, engine, color) {
        this.doors = doors;
        this.engine = engine;
        this.color = color;
    }

    stats() {
        console.log('doors:', this.doors, 'engine:', this.engine, 'color:', this.color);
    }
}

const cx5 = new Car(4, 'V6', 'grey');
cx5.stats();
```

## Inheritance
You can inherit only from one class.
```js
class SUV extends Car {
    constructor(doors, engine, color, brand) {
        super(doors, engine, color);
        this.brand = brand;
    }

    getBrand() {
        console.log('Thsi SUV is a '+this.brand)
    }
}

const cx5 = new SUV(4, 'V6', 'grey');
cx5.stats();
cx5.getBrand();

cx5 instanceof SUV // true
cx5 instanceof Car // true
```

## Mixins
If you want to inherit methods from more that one class you can use mixins. Mixins use composition over inheritance.
```js
let mixin = {
    madeIn() {
        console.log('Thisd car was made in year 2019');
    }
}

let carMixin = {
    __proto__ : mixin,

    madeIn() {
        super.madeIn();
    }
}

class SUV extends Car {
    constructor(doors, engine, color, brand) {
        super(doors, engine, color);
        this.brand = brand;

        Object.assign(this, carMixin);
    }

    getBrand() {
        console.log('Thsi SUV is a '+this.brand)
    }
}

const cx5 = new SUV(4, 'V6', 'grey');
cx5.stats();
cx5.getBrand();
cx5.madeIn();
```

## Accessor properties
There are two kind of properties into the object: data and accessor properties.

```js
class User {
    #email = null;
    set email (value) {
        if (!/@/.test(value)) throw new Еrrоr ('Incorrect email: $ { value }');
        this.#email = value;
    }

    get email ( ) {
        return this.#email;
    }
}

## Научи повече
- [Leveling up to ES6](https://www.udemy.com/leveling-up-to-es6/?ranMID=39197&ranEAID=bt30QTxEyjA&ranSiteID=bt30QTxEyjA-B6IyBFlf0sw_cqGr2SYJ0g&LSNPUBID=bt30QTxEyjA)