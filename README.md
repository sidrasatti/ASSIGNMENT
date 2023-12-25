# ASSIGNMENT
QUESTION NO 1


#include <iostream>
#include<string>
using namespace std;
class ElectronicDevice //abstract base class
{
public:
    virtual void turn_On() = 0;   // Pure virtual function
    virtual void turn_Off() = 0;  // Pure virtual function
};
//first derived class from base class in public mode
class Television : public ElectronicDevice
{
public:
    void turn_On()  //override
    {
        cout << "Television is turned on." << endl;
    }

    void turn_Off()
    {
        cout << "Television is turned off." << endl;
    }
};
//second class derived from base class in public mode
class Laptop : public ElectronicDevice
{
public:
    void turn_On()
    {
        cout << "Laptop is starting up." << endl;
    }

    void turn_Off()
    {
        cout << "Laptop is shutting down." << endl;
    }
};
int main()
{
    Television tv;
    Laptop laptop;
    ElectronicDevice* device1 = &tv;
    ElectronicDevice* device2 = &laptop;
    cout << "#####FOR TV #####" << endl;
    device1->turn_On();
    device1->turn_Off();
    cout << "##### FOR LAPTOP #####" << endl;
    device2->turn_On();
    device2->turn_Off();
    return 0;
}



QUESTION NO 2


#include <iostream>
#include <string>
using namespace std;
class Product
{
 public:
    Product() : productId(0), productName("Unknown"), price(0.0) {}
    int productId;
    string productName;
    double price;
     Product(int id, const string& name, double p) : productId(id), productName(name), price(p) {}
    void displayProductDetails()
    {
        cout << "Product ID: " << productId << ", Name: " << productName << ", Price: $" << price << endl;
    }
};
 class ShoppingCart
 {
   private:
    static const int maxCapacity = 5;
    Product products[maxCapacity];
    int size;
    double totalCost;
   public:
    ShoppingCart() : size(0), totalCost(0.0) {}
     void addProduct(const Product& product)
     {
        if (size < maxCapacity)
        {
            products[size++] = product;
            totalCost += product.price;
        }
          else
        {
            cout << "Shopping Cart is full. Cannot add more products." << endl;
        }
     }
         void displayAllProducts()
         {
           for (int i = 0; i < size; ++i)
           {
             products[i].displayProductDetails();
           }
         }
             double calculateTotalCost()
             {
                return totalCost;
             }
};
 class User
 {
   public:
   int userId;
    ShoppingCart* cart;
        User(int id) : userId(id), cart(nullptr) {}

    void displayUserDetails()
    {
        cout << "User ID: " << userId << endl;
    }
};

int main()
{

    ShoppingCart cart;
    Product p1(1, "washing machine", 10.99);
    Product p2(2, "refrigerator", 5.99);
    cart.addProduct(p1);
    cart.addProduct(p2);
    cout << "All Products in Cart:" << endl;
    cart.displayAllProducts();
    cout << "Total Cost: $" << cart.calculateTotalCost() << endl;
    User user1(101);
    user1.cart = &cart;
    user1.displayUserDetails();
    cout << "User's Cart Details:" << endl;
    user1.cart->displayAllProducts();
    return 0;
}
