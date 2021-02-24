
https://community.nxp.com/t5/i-MX-Processors/how-to-use-uuu-to-burn-imx6-NAND-flash-board/m-p/1024848/highlight/true



# C-Practice

## Class and Objects
#include <iostream>

using namespace std;

class First{
    public:
    void display(){
        std::cout << "Hii First" << std::endl;
    }
};

int main()
{
    
    First f;
    f.display();
    return 0;
}

Output:
Hii First

## Constructors
* Constructors automatically called when method of a class is created.
* It has no access specifier

#include <iostream>

using namespace std;

class First{
    public:
    First(){
        
        std::cout << "Hii First" << std::endl;    
        
    }
};

int main()
{
    
    First f;
    //f.display();
    return 0;
}

Output:
Hii First


Paramaterized constructor
#include <iostream>

using namespace std;

class First{
    public:
    First(int a, int b){
        int c=a+b;
        std::cout << "Hii First" << std::endl;
        std::cout << "The value of c: " << c << std::endl;
        
        
    }
};

int main()
{
    
    First f(5,10);
    //f.display();
    return 0;
}

Output:
Hii First
The value of c: 15

* Creating class objects and calling the constructor with different values

#include <iostream>

using namespace std;

class Person{
  public:
  string name;
  int height;
  char gender;
  string location;
  Person(string n, int h, char g, string l){
      name=n;
      height=h;
      gender=g;
      location=l;
  }
  
};

int main()
{
    Person p1("Rahul", 6, 'M', "Banglore");
    Person p2("Rina", 5, 'F', "Mysore");
    
    std::cout << p1.name << " " << p1.height << " " << p1.gender << " " << p1.location << " " <<  std::endl;
    std::cout << p2.name << " " << p2.height << " " << p2.gender << " " << p2.location << " " <<  std::endl;
    return 0;
}

Output:
Rahul 6 M Banglore                                                                                                                                   
Rina 5 F Mysore  

* Constructor defining outside a class

#include <iostream>

using namespace std;

class Person{
  public:
  string name;
  int height;
  char gender;
  string location;
  Person(string n, int h, char g, string l);
  
};
Person::Person(string n, int h, char g, string l){
      name=n;
      height=h;
      gender=g;
      location=l;
 }

int main()
{
    Person p1("Rahul", 6, 'M', "Banglore");
    Person p2("Rina", 5, 'F', "Mysore");
    
    std::cout << p1.name << " " << p1.height << " " << p1.gender << " " << p1.location << " " <<  std::endl;
    std::cout << p2.name << " " << p2.height << " " << p2.gender << " " << p2.location << " " <<  std::endl;
    return 0;
}

Output:
Rahul 6 M Banglore                                                                                                                                   
Rina 5 F Mysore  

## Access Specifier

C++ supports the feature of encapsulation in which the data is bundled together with the functions operating on it to form a single unit. By doing this C++ ensures that data is accessible only by the functions operating on it and not to anyone outside the class.

This is one of the distinguishing features of C++ that preserves the data and prevents it from leaking to the outside world.

The friend functions have the following properties:
There is no scope restriction for the friend function; hence, they can be called directly withot using objects.

Unlike member functions of class, the friend cannot access the member directly. On the other hand it uses object and dot operator to access the private and public member variables of the class.

By default, friendship is not shared(mutual). For example, if class X is declared as friend of Y, this does not meant that Y has privileges to access private members of class X.

Use of friend functions is rare, since it violates the rule of encapsulation and data hiding.

The function can be declared in public or private sections without changing its meaning.

#include <iostream>

class ac
{
private:
   char name[15];
   int accno;
   float bal;
public:
   void read()
   {
       std::cout << "\nName :";
       std::cin >> name; 
       std::cout << "\nA/c No. :";
       std::cin >> accno;
       std::cout << "\nBalance :";
       std::cin >> bal;
   }
   // Friend function declaration
   
   friend void showbal (ac);
};

void showbal (ac a)
{
   std:: cout << "\n Balance of A/c no. " << a.accno << "is Rs. " << a.bal;
}

int main()
{
   ac k;
   k.read();
   showbal(k);   // call to friend function
   return 0;
}

Output:
Name:Shreya
A/c No. : 911
Balance : 87695
Balance of A/c no. 911 is Rs.87695

> https://www.quora.com/What-are-some-situations-when-a-friend-function-can-be-useful-in-c++
> 
https://www.includehelp.com/cpp-tutorial/static-data-member-in-cpp-with-example.aspx
https://www.geeksforgeeks.org/static-keyword-cpp/


3


1
I am implementing my own linkedlist in C++ as part of a class assignment. My main concern isn't with the style of the code nor the pros/cons of including or not including certain features as I am still developing member functions.

I would mainly like to know if my approach of declaring LinkedList as a friend of Node is reasonable. My decision for doing this comes from the fact that there is absolutely no need for anything to access my Node class besides LinkedList (e.g. I don't want to be able to create a Node object in main). When I do this, however, I find myself no longer needing public and private access modifiers for Node. Furthermore, I don't particularly need getter/setter methods as I can just access Node's member variables directly from LinkedList (you can see below that I don't call Node::getVal() or Node::getNext() once).


Suppose, you need to operate on objects of two different class then,friend function can be very helpful. You can operate on two objects of different class without using friend function but, you program will be long, complex and hard to understand.
You can take this simple example further by considering a more complex class such as a Window. Quite likely a Window will have many function/data elements that should not be publicly accessible, but ARE needed by a related class such as a WindowManager.


dependancy in work



## Static

#include <iostream>
using namespace std;

// class First{
//     public:
    
    void counter(){
        int count=0;
        cout<<count<<" "<<endl;
        count++; 
        
    }
    
//};
int main() {
    // Write C++ code here
    //First f;
    for(int i=0;i<=5;i++){
        counter();    
    }
    

    return 0;
}

Output:

/tmp/BvViJyuuP4.o
0 
0 
0 
0 
0 
0 

Without using static variable- count is initializing every time.

#include <iostream>
using namespace std;

// class First{
//     public:
    
    void counter(){
        static int count=0;
        cout<<count<<" "<<endl;
        count++; 
        
    }
    
//};
int main() {
    // Write C++ code here
    //First f;
    for(int i=0;i<=5;i++){
        counter();    
    }
    

    return 0;
}
Output:
/tmp/BvViJyuuP4.o
0 
1 
2 
3 
4 
5 

After count as a static- once it initiallised scope of the variable remains their till the program get finished. It is taking previous value of the count at each turn.


#include <iostream>
using namespace std;

class First{
    public:
    static int count;             //int count; - Not applicable
    static void counter(){        //void counter() - Applicable
        
        cout<<count<<" "<<endl;
        count++; 
        
    }
    
    
};
int First:: count=0;
int main() {
    // Write C++ code here
    First f;
    for(int i=0;i<=5;i++){
        f.counter();    
    }
    

    return 0;
}

Output:
/tmp/BvViJyuuP4.o
0 
1 
2 
3 
4 
5 

Here, in above program we cant initialise and declare static variable together. We need to initialise outside the class. And static method can access static data as well as non static method also can access static data but non static data cant be accessed by static method.

### This Keyword

If local variable and function argument name is same then this keyword is used to distinguiesh the both them. As well as this keyword is used to display the value which is passed by function.

#include <iostream>
using namespace std;


class This{
    public:
   
    string name;
    int age;
    void getInfo(string name, int age){
        
        name=name;
        age=age;
    }
    void display(){
        cout<<"Name: "<<name<<endl;
        cout<<"Age: "<<age<<endl;
    }
};
int main() {
    This t1;
    t1.getInfo("Ayan", 20);
    t1.display();
    return 0;
}

Output:
/tmp/UO1JCBXeRl.o
Name: 
Age: 0
In this program 

Scenario 2
#include <iostream>
using namespace std;


class This{
    public:
    string name="Aditya";
    int age=21;
    //string name;
    //int age;
    void getInfo(string name, int age){
        //this->name=name;
        //this->age=age;
        name=name;
        age=age;
    }
    void display(){
        cout<<"Name: "<<name<<endl;
        cout<<"Age: "<<age<<endl;
    }
};
int main() {
    This t1;
    t1.getInfo("Ayan", 20);
    t1.display();
    return 0;
}

Output:
/tmp/UO1JCBXeRl.o
Name: Aditya
Age: 21

Scenario 3
#include <iostream>
using namespace std;


class This{
    public:
    //string name="Aditya";
    //int age=21;
    string name;
    int age;
    void getInfo(string name, int age){
        this->name=name;
        this->age=age;
        //name=name;
        //age=age;
    }
    void display(){
        cout<<"Name: "<<name<<endl;
        cout<<"Age: "<<age<<endl;
    }
};
int main() {
    This t1;
    t1.getInfo("Ayan", 20);
    t1.display();
    return 0;
}

Output:
/tmp/UO1JCBXeRl.o
Name: Ayan
Age: 20

Scenario 4





### Virtual function

Rules of Virtual Function
* Virtual functions must be members of some class.
* Virtual functions cannot be static members.
* They are accessed through object pointers.
* They can be a friend of another class.
* A virtual function must be defined in the base class, even though it is not used.
* The prototypes of a virtual function of the base class and all the derived classes must be identical. If the two functions with the same name but different prototypes, C++ will consider them as the overloaded functions.
* We cannot have a virtual constructor, but we can have a virtual destructor
* Consider the situation when we don't use the virtual keyword.
    #include <iostream>  
    using namespace std;  
    class A  
    {  
       int x=5;  
        public:  
        void display()  
        {  
            std::cout << "Value of x is : " << x<<std::endl;  
        }  
    };  
    class B: public A  
    {  
        int y = 10;  
        public:  
        void display()  
        {  
            std::cout << "Value of y is : " <<y<< std::endl;  
        }  
    };  
    int main()  
    {  
        A *a;  
        B b;  
        a = &b;  
       a->display();  
        return 0;  
    }  
    
    Output:
    Value of x is : 5
    
    In the above example, * a is the base class pointer. The pointer can only access the base class members but not the members of the derived class. Although C++ permits the base pointer to point to any object derived from the base class, it cannot directly access the members of the derived class. Therefore, there is a need for virtual function which allows the base pointer to access the members of the derived class.
    
    With virtual function
       #include <iostream>    
    {    
     public:    
     virtual void display()    
     {    
      cout << "Base class is invoked"<<endl;    
     }    
    };    
    class B:public A    
    {    
     public:    
     void display()    
     {    
      cout << "Derived Class is invoked"<<endl;    
     }    
    };    
    int main()    
    {    
     A* a;    //pointer of base class    
     B b;     //object of derived class    
     a = &b;    
     a->display();   //Late Binding occurs    
    }    
    
    Output:
    Derived Class is invoked 
    
> Why virtual function
Virtual Functions are used to support Runtime Polymorphism. ... When the virtual function is called by using a Base class pointer, the compiler decides at run-time which version of the function - i.e. the Base class version or the overridden Derived class version - is to be called. This is called Runtime Polymorphism.

### pure virtual function and abstarct class
A pure virtual function is a virtual function in C++ for which we need not to write any function definition and only we have to declare it. It is declared by assigning 0 in the declaration.

* An abstract class is a class in C++ which have at least one pure virtual function.

* Abstract class can have normal functions and variables along with a pure virtual function.

* Abstract class cannot be instantiated, but pointers and references of Abstract class type can be created.

* Abstract classes are mainly used for Upcasting, so that its derived classes can use its interface.

* If an Abstract Class has derived class, they must implement all pure virtual functions, or else they will become Abstract too.

* We can’t create object of abstract class as we reserve a slot for a pure virtual function in Vtable, but we don’t put any address, so Vtable will remain incomplete.


> Why we are using
Sometimes implementation of all function cannot be provided in a base class because we don’t know the implementation. Such a class is called abstract class. For example, let Shape be a base class. We cannot provide implementation of function draw() in Shape, but we know every derived class must have implementation of draw(). Similarly an Animal class doesn’t have implementation of move() (assuming that all animals move), but all animals must know how to move. We cannot create objects of abstract classes.


#include<iostream> 
using namespace std; 
  
class Base 
{ 
   int x; 
public: 
    virtual void fun() = 0; 
    int getX() { return x; } 
}; 
  
// This class inherits from Base and implements fun() 
class Derived: public Base 
{ 
    int y; 
public: 
    void fun() { cout << "fun() called"; } 
}; 
  
int main(void) 
{ 
    Derived d; 
    d.fun(); 
    return 0; 
} 

Output:
fun() called

* Some Interesting Facts:

1)  A class is abstract if it has at least one pure virtual function.
In the following example, Test is an abstract class because it has a pure virtual function show().

#include<iostream> 
using namespace std; 
  
class Test 
{ 
   int x; 
public: 
    virtual void show() = 0; 
    int getX() { return x; } 
}; 
  
int main(void) 
{ 
    Test t; 
    return 0; 
} 

Output:

Compiler Error: cannot declare variable 't' to be of abstract
 type 'Test' because the following virtual functions are pure 
within 'Test': note:     virtual void Test::show() 

2) 2) We can have pointers and references of abstract class type.
For example the following program works fine.

#include<iostream> 
using namespace std; 
  
class Base 
{ 
public: 
    virtual void show() = 0; 
}; 
  
class Derived: public Base 
{ 
public: 
    void show() { cout << "In Derived \n"; } 
}; 
  
int main(void) 
{ 
    Base *bp = new Derived(); 
    bp->show(); 
    return 0; 
}

Output:

In Derived 

3) If we do not override the pure virtual function in derived class, then derived class also becomes abstract class.
The following example demonstrates the same.

#include<iostream> 
using namespace std; 
class Base 
{ 
public: 
    virtual void show() = 0; 
}; 
  
class Derived : public Base { }; 
  
int main(void) 
{ 
  Derived d; 
  return 0; 
}

Output:

Compiler Error: cannot declare variable 'd' to be of abstract type 
'Derived'  because the following virtual functions are pure within
'Derived': virtual void Base::show() 
4) An abstract class can have constructors.
For example, the following program compiles and runs fine.

#include<iostream> 
using namespace std; 
  
// An abstract class with constructor 
class Base 
{ 
protected: 
   int x; 
public: 
  virtual void fun() = 0; 
  Base(int i) { x = i; } 
}; 
  
class Derived: public Base 
{ 
    int y; 
public: 
    Derived(int i, int j):Base(i) { y = j; } 
    void fun() { cout << "x = " << x << ", y = " << y; } 
}; 
  
int main(void) 
{ 
    Derived d(4, 5); 
    d.fun(); 
    return 0; 
} 

Output:

x = 4, y = 5



