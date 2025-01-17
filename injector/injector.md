# Python `injector` Library

The **`injector`** library in Python is a dependency injection framework that helps manage object creation and dependency management, making code more modular and testable. It is inspired by dependency injection systems from other programming languages like Java's Guice.

---

### **Core Concepts**
1. **Injector**: The main class responsible for providing dependencies.
2. **Modules**: Classes that configure how objects are created and bound to interfaces.
3. **Bindings**: Define how a particular dependency should be resolved.
4. **Providers**: Functions or factories to create complex dependencies.

---

### **Installation**
```bash
pip install injector
```

---

### **Example of usage**
#### Basic Dependency injection

```python
from injector import Injector, inject, Module, provider, singleton

# Define a service class
class Logger:
    def log(self, message: str):
        print(f"LOG: {message}")

# Define another service that depends on Logger
class Service:
    @inject
    def __init__(self, logger: Logger):
        self.logger = logger
    
    def perform_action(self):
        self.logger.log("Action performed!")

# Set up the injector and provide the bindings
injector = Injector()
service = injector.get(Service)
service.perform_action()
```

#### Explanation
- The Injector automatically resolves the dependencies for Service by creating a Logger instance and injecting it into Service.
- The @inject decorator indicates that dependencies for Service should be automatically injected.

---

### Using Modules to Configure Bindings
Modules are useful for more complex configurations.

```python
class ConfigModule(Module):
    @singleton
    @provider
    def provide_logger(self) -> Logger:
        # Custom configuration or object creation can go here
        return Logger()

injector = Injector([ConfigModule()])
service = injector.get(Service)
service.perform_action()
```

---

### Features
1. Scope Management: Use @singleton to make an object shared across all requests.
2. Custom Providers: Define how dependencies are constructed.
3. Automatic Resolution: Injector resolves dependencies by inspecting type annotations.

---

### When to Use Injector
- Large projects where class dependencies are complex.
- Scenarios where testing is essential, and mocks or stubs are frequently required.
- Building scalable, loosely coupled architectures.
