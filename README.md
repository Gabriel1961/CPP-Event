# CPP-Event(A C# Action class implementation)
This is an implementation of the C# Action Class in C++. It features subscribing to global functions, class member functions as well as lambdas.
As of currently it supports three parameter arguments, but it could be easily extended. 

## Quick Setup
Download the Action.h file, from the repository and than just add it to your project solution followed by this:
```C++
#include "Action.h"
```
##Example

> Creating a event 
```C++
using namespace EventSystem;
int main()
{
    Action action;
    Action<int> action; // template types represent the types of the parameters
    Action<int,string> action;
    Action<double,int,const char*> action;
}

```
