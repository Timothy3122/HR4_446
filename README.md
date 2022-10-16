# HR4_446

##Inheritance Introduction
```
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;


class Triangle{
    public:
    	void triangle(){
     		cout<<"I am a triangle\n";
    	}
};

class Isosceles : public Triangle{
    public:
    	 void isosceles(){
          cout<<"I am an isosceles triangle\n";
       }
    
       void description(){
          cout<<"In an isosceles triangle two sides are equal\n";
       }
};

int main(){
    Isosceles isc;
    isc.isosceles();
  	isc.description();
    isc.triangle();
    return 0;
}
```

##Accessing Inherited Functions
```
class D : public A,public B,public C
{

  int val;
  public:
  //Initially val is 1
  D()
  {
    val=1;
  }



  void update_val(int new_val)
  {
    while (new_val!=val) {
      if (new_val/val % 2 == 0) A::func(val);
      else if (new_val/val % 3 == 0) B::func(val);
      else if (new_val/val % 5 == 0) C::func(val);
    }
  }
  
  void check(int);
};
```

##Inherited Code
```
class BadLengthException : exception {
    int len;
    
    public:
    BadLengthException(int l): len (l) {}
    string what() { return to_string(len); }
};
```

##Multilevel Inheritance
```
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

class Triangle{
   public:
      void triangle(){
         cout<<"I am a triangle\n";
      }
};

class Isosceles : public Triangle{
     public:
        void isosceles(){
          cout<<"I am an isosceles triangle\n";
        }
};

class Equilateral :public Isosceles{
    public:
    void equilateral(){
        cout<<"I am an equilateral triangle\n";
    }
};
   
//Write your code here.
int main(){
    Equilateral eqr;
    eqr.equilateral();
    eqr.isosceles();
    eqr.triangle();
    return 0;
}
```

##Abstract Classes-Polymorphism
```
class LRUCache: public Cache
{
public:
    LRUCache(int c) 
    {
      cp = c;
    }

    void set(int k, int v) 
    {
        Node* N;

        if ( mp.empty() ) 
        {

            N = new Node(k,v);
            tail = head = N;
            mp[k] = N;

            return;
        }
        auto it = mp.find(k);
        if ( it != mp.end() ) 
        {
            it->second->value = v;
            if ( head == it->second ) 
            {
                return;
            }
            it->second->prev->next = it->second->next;           
            if ( tail == it->second ) 
            {
                tail = tail->prev;
            }
            else 
            {               
                it->second->next->prev = it->second->prev;
            }           
            it->second->next = head;
            it->second->prev = nullptr;
            head->prev = it->second;
            head = it->second;
        }
        else 
        {
            N = new Node(head->prev, head, k, v);
            head->prev = N; 
            head = N;
            mp[k] = N;
            if ( mp.size() > cp ) 
            {
                tail = tail->prev;
                mp.erase(tail->next->key);
                delete tail->next; 
                tail->next = nullptr;
            }
        }
    }
    int get(int k) 
    {
        auto it = mp.find(k);
        if ( it != mp.end() ) 
        {
            return it->second->value;
        }
        
        return -1;
    }
};
```

