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



