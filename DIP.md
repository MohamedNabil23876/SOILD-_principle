


```cpp



class MotorDriver {  
public:  
void move() {}  
};  
  
class Robot {  
MotorDriver motor;  
};








class Motor {  
public:  
    virtual void move() = 0;  
};


class L298Motor : public Motor {  
public:  
    void move() override {}  
};



class Robot {  
    Motor* motor;  
  
public:  
    Robot(Motor* m) : motor(m) {}  
  
    void moveRobot() {  
        motor->move();  
    }  
};



class Paymentmethid {  
public:  
   virtual  void pay() =0
};  
  

class applypayment :Paymentmethid
{
  piblic :
  void pay(){
  }
  
}
 
class PaymentProcessor {  
    Paymentmethid   * payment;  
public:  
    void PaymentProcessor(Paymentmethid   * pay):payment(pay)
    {
    payment -> pay();
    }
};












#include <iostream>
#include <string>

// =======================
// Abstraction / Interface
// =======================
class InputDevice {
public:
    virtual std::string getInput() = 0;
    virtual ~InputDevice() = default;
};

// =======================
// Low-level Modules
// =======================
class Keyboard : public InputDevice {
public:
    std::string getInput() override { 
        return "Keyboard Input"; 
    }
};

class Mouse : public InputDevice {
public:
    std::string getInput() override { 
        return "Mouse Input"; 
    }
};

// =======================
// High-level Module
// =======================
class Computer {
public:
    // Dependency Injection via constructor
    Computer(InputDevice &device) : inputDevice(device) {}

    void processInput() {
        std::string input = inputDevice.getInput();
        std::cout << "Processing: " << input << std::endl;
    }

private:
    InputDevice &inputDevice;
};

// =======================
// Main Function
// =======================
int main() {
    Keyboard k;
    Mouse m;

    Computer comp1(k); 
    comp1.processInput(); // Output: Processing: Keyboard Input

    Computer comp2(m); 
    comp2.processInput(); // Output: Processing: Mouse Input

    return 0;
}
```

---


