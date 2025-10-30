#include <iostream>
using namespace std;

class Box {
private:
    double width;

public:
    // Constructor
    Box(double w = 0.0) : width(w) {}

    // Declare a friend function
    friend void printWidth(const Box& b);
    friend class BoxManager; // Declare a friend class
};

// Friend function definition
void printWidth(const Box& b) {
    cout << "Width of box: " << b.width << endl;  // Accessing private member
}

// Friend class example
class BoxManager {
public:
    void doubleWidth(Box& b) {
        b.width *= 2;  // Accessing private member of Box
    }
};

int main() {
    Box b1(5.0);
    printWidth(b1);  // Friend function can access private data

    BoxManager manager;
    manager.doubleWidth(b1); // Friend class accessing private member
    printWidth(b1);  // Display updated width

    return 0;
}
