
```cpp
// ❌ FAT INTERFACE: forces all implementors to define all methods
class IWorker {
public:
    virtual void work()   = 0;
    virtual void eat()    = 0;  // Robots don't eat!
    virtual void sleep()  = 0;  // Robots don't sleep!
    virtual ~IWorker() = default;
};

class HumanWorker : public IWorker {
public:
    void work()  override { std::cout << "Human working\n"; }
    void eat()   override { std::cout << "Human eating\n";  }
    void sleep() override { std::cout << "Human sleeping\n"; }
};

// ❌ Robot is forced to implement eat() and sleep() — meaningless for it
class RobotWorker : public IWorker {
public:
    void work()  override { std::cout << "Robot working\n"; }
    void eat()   override { /* DOES NOTHING — ISP violation */ }
    void sleep() override { /* DOES NOTHING — ISP violation */ }
};
```


```cpp
#include <iostream>

// Segregated interfaces — each represents one coherent capability
class IWorkable {
public:
    virtual void work() = 0;
    virtual ~IWorkable() = default;
};

class IFeedable {
public:
    virtual void eat() = 0;
    virtual ~IFeedable() = default;
};

class IRestable {
public:
    virtual void sleep() = 0;
    virtual ~IRestable() = default;
};

// Human implements ALL three interfaces
class HumanWorker : public IWorkable, public IFeedable, public IRestable {
public:
    void work()  override { std::cout << "Human: working diligently\n"; }
    void eat()   override { std::cout << "Human: eating lunch\n"; }
    void sleep() override { std::cout << "Human: sleeping 8 hours\n"; }
};

// Robot only implements what it needs
class RobotWorker : public IWorkable {
public:
    void work() override { std::cout << "Robot: executing task 24/7\n"; }
    // No eat(), no sleep() — clean, correct, honest
};

// Client functions depend only on the interfaces they need
void assignWork(IWorkable& worker) {
    worker.work();
}

void feedEmployee(IFeedable& employee) {
    employee.eat();
}

int main() {
    HumanWorker human;
    RobotWorker robot;

    assignWork(human);  // OK
    assignWork(robot);  // OK
    feedEmployee(human); // OK
    // feedEmployee(robot); // COMPILE ERROR — correct! Robots don't eat.
    return 0;
}
```


