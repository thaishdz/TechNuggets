

# Hexagonal Architecture


Imagine hexagonal architecture as a pattern that separates __the core application from external services__ like _databases_ and _user interfaces_.


![image](https://github.com/user-attachments/assets/0bf5ea91-fc9c-4544-916d-af72acf130de)


- The application __domain lives inside the hexagon__.
- Business logic follows __domain-driven design (DDD) principles__, which means it shouldn’t leak outside the hexagon.

- __Ports are interfaces__ through which the application interacts with external services. 
- __While Adapters are implementations of the ports__. 

This means ports define the contract or interface.
While adapters provide implementation to fulfill the contract.



# Ayuditas 🛎️

- [How McDonald’s Food Delivery Platform Handles 20,000 Orders per Second](https://medium.com/@ahmadsadiq885/how-mcdonalds-food-delivery-platform-handles-20-000-orders-per-second-578d8d10b976)
