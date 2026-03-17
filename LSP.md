

```cpp
Shape
```

 subclasses:

```cpp
Circle
Rectangle
Triangle
```


```cpp
Shape*
```

```cpp
Circle
Rectangle
Triangle
```




## Base Class

```cpp
class Rectangle {
protected:
    int width;
    int height;

public:

    virtual void setWidth(int w) {
        width = w;
    }

    virtual void setHeight(int h) {
        height = h;
    }

    int area() {
        return width * height;
    }
};
```

```cpp
class Square : public Rectangle {

public:

    void setWidth(int w) override {
        width = height = w;
    }

    void setHeight(int h) override {
        width = height = h;
    }
};
```

```cpp
void test(Rectangle& r)
{
    r.setWidth(5);
    r.setHeight(4);

    std::cout << r.area();
}
```



## Shape Interface

```cpp
class Shape
{
public:
    virtual int area() = 0;
};
```

```cpp
class Rectangle : public Shape
{
    int w, h;

public:

    Rectangle(int w , int h) : w(w) , h(h) {}

    int area() override
    {
        return w * h;
    }
};
```

---

## Square

```cpp
class Square : public Shape
{
    int side;

public:

    Square(int s) : side(s) {}

    int area() override
    {
        return side * side;
    }
};
```


```cpp
Shape* s1 = new Rectangle(5,4);
Shape* s2 = new Square(4);
```





```cpp
class Bird {
public:
    virtual void fly() { std::cout << "Flying!\n"; }
};

class Penguin : public Bird {
public:
    // ❌ Penguins can't fly — violates the Bird contract!
    void fly() override {
        throw std::logic_error("Penguins can't fly!");
    }
};

void makeBirdFly(Bird& b) {
    b.fly(); // Will throw if passed a Penguin — LSP violated
}
```



```cpp
class Bird      { public: virtual void eat()  { /* ... */ } };
class FlyingBird : public Bird { public: virtual void fly() = 0; };
class Penguin   : public Bird  { /* no fly() */ };
class Eagle     : public FlyingBird { public: void fly() override { /* ... */ } };
```


