

```cpp
class PaymentProcessor {
public:

    void processPayment(std::string type) {

        if(type == "creditcard") {
            std::cout << "Processing credit card\n";
        }

        else if(type == "paypal") {
            std::cout << "Processing PayPal\n";
        }
        else if(type == "applepay") {
            std::cout << "Processing applepay\n";
        }
        
       

    }
};
```









# Interface

```cpp
class PaymentMethod {
public:
    virtual void pay() = 0;
};
class CreditCardPayment : public PaymentMethod {
public:
    void pay() override {
        std::cout << "Processing Credit Card\n";
    }
};
class PayPalPayment : public PaymentMethod {
public:
    void pay() override {
        std::cout << "Processing PayPal\n";
    }
};

class PaymentProcessor {
public:

    void process(PaymentMethod* payment) {
        payment->pay();
    }
};
```


```cpp
int main() {

    PaymentProcessor processor;

    CreditCardPayment card;
    PayPalPayment paypal;

    processor.process(&card);
    processor.process(&paypal);
}
```



```cpp
class ApplePayPayment : public PaymentMethod {
public:
    void pay() override {
        std::cout << "Processing Apple Pay\n";
    }
};
```




```cpp
class SensorReader {

public:

    void read(std::string type) {

        if(type == "temperature") {}

        else if(type == "pressure") {}

        else if(type == "humidity") {}
    }
};
```


```cpp
class Sensor {
public:
    virtual void read() = 0;
};
```

وبعدين:

```cpp
TemperatureSensor
PressureSensor
HumiditySensor
```
