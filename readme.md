# 3.1 Class and object

**Date : 7/11/23**

1. Class code example:
    
    ```tsx
    // OOP class
    class Animal {
        public name: string;
        public species: string;
        public sound: string;
        constructor(name: string,species: string,sound: string){
            this.name = name
            this.species = species
            this.sound = sound
        }
        makeSound(){
            console.log(`The ${this.name} says ${this.sound}`)
        }
    }
    
    const dog = new Animal("German shepard  bhai", "dog","Ghew Ghew")
    const cat = new Animal("Persian bhai", "cat","meaw meaw")
    
    console.log(dog);
    console.log(cat);
    ```
    
2. Class code more simplified:
    
    ```tsx
    {
      // OOP class
      class Animal {
        // parameter properties
        constructor(public name: string, public species: string,public sound: string) {}
        makeSound() {
          console.log(`The ${this.name} says ${this.sound}`);
        }
      }
    
      const dog = new Animal("German shepard  bhai", "dog", "Ghew Ghew");
      const cat = new Animal("Persian bhai", "cat", "meaw meaw");
    
      console.log(dog);
      console.log(cat);
    }
    ```
    

## Reference:
1. Typescript class docs:
[TypeScript Classes](https://www.tutorialsteacher.com/typescript/typescript-class)

# 3.2 - Inheritance in OOP

**Date: 6/11/23**

1. {Class Practice} Inheritance Code example:
    
    ```tsx
    {
      // OOP - Inheritance
      // parent class of Person
      class Person {
        name: string;
        age: number;
        address: string;
        constructor(name: string, age: number, address: string) {
          this.name = name;
          this.age = age;
          this.address = address;
        }
        getSleep(numOfHour: number) {
          console.log(`${this.name} will sleep for ${numOfHour} hour`);
        }
      }
      // student inherit Person Class
      class Student extends Person {
        RollNo: number;
        constructor(name: string, age: number, address: string, RollNo: number) {
          super(name, age, address);
          this.RollNo = RollNo;
        }
        getRead(numOfHourRead: number){
            console.log(`${this.name} everyday total ${numOfHourRead} hour read`);
        }
      }
      // Teacher inherit Person Class
      class Teacher extends Person {
        designation: string;
        constructor(
          name: string,
          age: number,
          address: string,
          designation: string
        ) {
          super(name, age, address);
          this.designation = designation;
        }
        takeClass(numOfClass: number) {
          console.log(`${this.name} will take ${numOfClass}`);
        }
      }
      const student1 = new Student("Mr. Rayhan", 20, "Bangladesh",1);
      const teacher1 = new Teacher("Mr. sabbir", 50, "Bangladesh", "professor");
    
      student1.getSleep(8);
      student1.getRead(5)
      teacher1.takeClass(5);
    }
    ```
    
    1. {Class Practice} inheritance code more simplified:
    
    ```tsx
    {
      // OOP - Inheritance
      // parent class of Person
      class Person {
        constructor(
          public name: string,
          public age: number,
          public address: string
        ) {}
        getSleep(numOfHour: number) {
          console.log(`${this.name} will sleep for ${numOfHour} hour`);
        }
      }
      // student inherit Person Class
      class Student extends Person {
        constructor(
          name: string,
          age: number,
          address: string,
          public RollNo: number
        ) {
          super(name, age, address);
        }
        getRead(numOfHourRead: number) {
          console.log(`${this.name} everyday total ${numOfHourRead} hour read`);
        }
      }
      // Teacher inherit Person Class
      class Teacher extends Person {
        constructor(
          name: string,
          age: number,
          address: string,
          public designation: string
        ) {
          super(name, age, address);
        }
        takeClass(numOfClass: number) {
          console.log(`${this.name} will take ${numOfClass}`);
        }
      }
      const student1 = new Student("Mr. Rayhan", 20, "Bangladesh", 1);
      const teacher1 = new Teacher("Mr. sabbir", 50, "Bangladesh", "professor");
    
      student1.getSleep(8);
      student1.getRead(5);
      teacher1.takeClass(5);
    }
    ```
    
    ## Reference:
    
1. Typescript Inheritance docs:
[TypeScript Inheritance](https://www.typescripttutorial.net/typescript-tutorial/typescript-inheritance/)

[TypeScript Inheritance - GeeksforGeeks](https://www.geeksforgeeks.org/typescript-inheritance/)

# 3.3 - ****Type guard using typeof & in****

**Date : 7/11/23**

1. typeof & in guard use in typescript code example:
```tsx
  {
    // type guards

    // typeof --> type guard
    type Alphanumeric = string | number

    const add = (param1: Alphanumeric,param2 : Alphanumeric) : Alphanumeric  => {   
        if(typeof param1 === 'number' && typeof param2 === 'number'){
            return param1 + param2
        }else {
            return param1.toString() + param2.toString()
        }
    }
    const result1 = add('3', '5')
    const result2 = add(5,5)
    console.log(result1);
    console.log(result2);

    // in --> in guard
    type NormalUser = {
        name: string
    }

    type AdminUser = {
        name: string;
        role: 'admin'
    }

    const getUser = (user: NormalUser | AdminUser) : string => {
        if('role' in user){
            return `My name is ${user.name} and my role is ${user.role}`
        }else {
            return `My name is ${user.name}`
        }
    }

    const normalUser: NormalUser = {
        name: 'Rahat hossain'
    }
    const adminUser: AdminUser = {
        name: 'Rayhan Mojumdar',
        role: 'admin'
    }

    const user1 = getUser(normalUser)
    const user2 = getUser(adminUser)

    console.log(user1);
    console.log(user2);

}
```