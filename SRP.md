

```cpp
#include <iostream>
using namespace std;

class Order
{
public:

    void calculateTotal()
    {
        cout << "Calculating total price\n";
    }

    void saveToDatabase()
    {
        cout << "Saving order to database\n";
    }

    void printInvoice()
    {
        cout << "Printing invoice\n";
    }
};

int main()
{
    Order order;

    order.calculateTotal();
    order.saveToDatabase();
    order.printInvoice();
}
```






### Order class

```cpp
class Order
{
public:
    void calculateTotal()
    {
        cout << "Calculating total price\n";
    }
};
class OrderRepository
{
public:
    void save(Order& order)
    {
        cout << "Saving order to database\n";
    }
};

class InvoicePrinter
{
public:
    void print(Order& order)
    {
        cout << "Printing invoice\n";
    }
};
int main()
{
    Order order;

    OrderRepository repo;
    InvoicePrinter printer;

    order.calculateTotal();
    repo.save(order);
    printer.print(order);
}
```

---



```cpp
class TemperatureSystem
{
public:

    void readSensor() {}

    void displayOnLCD() {}

    void sendUART() {}
};
```




```cpp
class UserManager
{
public:
    void addUser(){}
    void deleteUser(){}
    void saveToFile(){}
    void sendEmail(){}
};
```



```cpp
class Report {
public:

    void generateData() {
        // business logic
    }

    void formatHTML() {
        // UI formatting
    }
};
```

