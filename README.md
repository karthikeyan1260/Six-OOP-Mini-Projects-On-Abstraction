# 🧩 Abstraction in Python: 6 OOP Mini Projects

A collection of six small, real-world-inspired systems that demonstrate **abstraction** in Python using the `abc` module. Each project defines an abstract base class as a contract and implements it through multiple child classes.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)
![OOP](https://img.shields.io/badge/Concept-Abstraction-green)

---

## 📌 Overview

In real applications, the same task is often done in many different ways: a notification can go out by email, SMS, or push; a payment can be made through UPI, card, or PayPal. Abstraction lets us define **what** must be done in one place and leave **how** it is done to each implementation.

This repository contains six mini projects (all in `Abstraction_Task.ipynb`), each showing this idea in a different scenario.

## ❓ Problem Statement

Without a common structure, code that handles multiple variants of the same behavior becomes repetitive, hard to extend, and easy to break. The goal of this project is to solve that using abstraction so that:

- Every implementation follows the same contract
- New implementations can be added without changing existing code
- Client code works with any implementation through one common interface

## 🛠️ Technology Stack

| Category | Details |
| --- | --- |
| Language | Python 3 |
| Concepts | Abstraction, Inheritance, Polymorphism |
| Module | `abc` (`ABC`, `@abstractmethod`) |
| Environment | Jupyter Notebook |

## 📂 Projects Included

| # | Project | Abstract Class | Implementations |
| --- | --- | --- | --- |
| 1 | Notification Service | `Notifier` | `Email`, `SMS`, `PushNotification` |
| 2 | Database Repository | `UserRepository` | `PostgreSQL`, `MongoDB` |
| 3 | File System Storage | `FileStorage` | `LocalStorage`, `AWSS3`, `GoogleCloud`, `AzureBlob` |
| 4 | Vehicle System | `Vehicle` | `Car`, `Bike`, `ElectricScooter`, `Bus` |
| 5 | Report Generator | `ReportExporter` | `CSVExporter`, `JSONExporter`, `ExcelExporter`, `PDFExporter` |
| 6 | Payment Gateway | `PaymentGateway` | `UPIPayment`, `CardPayment`, `PayPalPayment` |

> **Note:** The implementations are simulated with `print` statements and return strings. The focus is on design and structure, not on integrating real services.

## ⚙️ How It Works

**1. Define the contract with an abstract class**

```python
from abc import ABC, abstractmethod

class PaymentGateway(ABC):

    @abstractmethod
    def pay(self, amount):
        pass

    @abstractmethod
    def refund(self, transaction_id):
        pass
```

**2. Implement it in child classes**

```python
class UPIPayment(PaymentGateway):

    def pay(self, amount):
        return f"Paid Rs.{amount} through UPI"

    def refund(self, transaction_id):
        return f"UPI refund initiated for {transaction_id}"
```

**3. Write client code that works with any implementation**

```python
def checkout(gateway, amount):
    print(gateway.pay(amount))

checkout(UPIPayment(), 999)
checkout(CardPayment(), 2499)
checkout(PayPalPayment(), 49.99)
```

`checkout()` never needs to know which gateway it receives, which is the power of abstraction combined with polymorphism.

**4. Mix abstract and concrete methods**

The Vehicle System shows that an abstract class can also provide shared behavior:

```python
class Vehicle(ABC):

    @abstractmethod
    def start(self):
        pass

    @abstractmethod
    def stop(self):
        pass

    # Normal method inherited by all child classes
    def vehicle_info(self):
        print(f"This is a {self.__class__.__name__}")
```

## 🚀 Getting Started

**Prerequisites**

- Python 3.x
- Jupyter Notebook or JupyterLab (or VS Code with the Jupyter extension)

**Run locally**

```bash
# Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

# Install Jupyter (if needed)
pip install notebook

# Launch the notebook
jupyter notebook Abstraction_Task.ipynb
```

Run the cells from top to bottom to see the output of each project.

## 📸 Sample Output

```text
Paid Rs.999 through UPI
Paid Rs.2499 using Card
Paid $49.99 using PayPal

UPI refund initiated for UPI101
Card refund initiated for CARD102
PayPal refund initiated for PAYPAL103
```

## 💡 Key Learnings

- An abstract class **cannot be instantiated** directly, and any child class that skips an abstract method raises a `TypeError`. The contract is enforced.
- Abstraction makes **polymorphism** practical: one loop can call `start()` on a Car, Bike, and Bus.
- Adding a new option, such as a new payment method, means adding a new class rather than rewriting existing code.
- Abstract classes can hold both abstract and concrete methods, which helps avoid duplicated code.
- Good design separates the **"what"** from the **"how."**

## 🌍 Real-World Use Cases

- **Notifications:** email, SMS, and push services behind one interface
- **Payments:** UPI, cards, and wallets through a single checkout flow
- **Databases:** swapping PostgreSQL for MongoDB using the repository pattern
- **Cloud storage:** switching between local, AWS S3, Google Cloud, and Azure
- **Reporting:** exporting the same data as CSV, JSON, Excel, or PDF

## 🔮 Future Improvements

- Add real integrations (SMTP for email, a payment sandbox API, a database driver)
- Add error handling and input validation
- Write unit tests for each implementation
- Use a factory pattern to select implementations at runtime

## 🤝 Contributing

Suggestions and improvements are welcome. Feel free to fork the repository and open a pull request.

## 👤 Author

**Karthikeyan**
Chennai, India

- LinkedIn: [your-linkedin-profile](https://www.linkedin.com/in/karthikeyans12)
- GitHub: [your-username](https://github.com/karthikeyans1260)

---

⭐ If you found this helpful, consider giving the repository a star!
