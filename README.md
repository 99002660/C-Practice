
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
