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



