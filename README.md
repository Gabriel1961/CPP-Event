# CPP-Event(A C# Action class implementation)
This is an implementation of the C# Action Class in C++. It features subscribing to global functions, class member functions as well as lambdas.
As of currently it supports three parameter arguments, but it could be easily extended. 

## Quick Setup
Download the Action.h file, from the repository and than just add it to your project solution followed by this:
```C++
#include "Action.h"
```

## Example

> Creating a event 
```C++
using namespace EventSystem;
int main()
{
    Action action; // No parameters 
    Action<int> action; // template types represent the types of the parameters
    Action<int,string> action;
    Action<double,int,const char*> action;
}

```

> Subscribing to an event

```C++
void PrintStuff(int a)
{
    std::cout << a << endl;
}

>Triggering the event

```C++
int main 
{
    Action<int> action;
    action += [](int a){ PrintStuff(a);}; 
    action(1); // or you can do action.Call(1);
    // in parenthesis are the parameters requiered to run the functions subscribed to the event
}
```

```
Output:
1
```

int main()
{
    Action<int> action;
    action += PrintStuff; // subscribe to the event
    action += [](int a){ PrintStuff(a);}; // also works with a lambda expression
}
```

>Subscribing with a member function to an event

```C++
class Foo
{
public:
	int id;
	Foo(int id)
		:id(id)
	{
	}

	void PrintStuff(int param)
	{
		std::cout << id << " : " << param << endl;
	}
};

int main()
{
	Action<int> action;
	Foo foo(3);
	action.SubscribeMethod(&Foo::PrintStuff, foo);
	action.Call(1);
}
```
