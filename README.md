import injector

# Define some classes
class Service:
    def __init__(self, name):
        self.name = name

class Client:
    def __init__(self, service):
        self.service = service

# Define a module
class MyModule(injector.Module):
    def configure(self, binder):
        binder.bind(Service, to=Service('MyService'))

# Create an injector
injector_instance = injector.Injector([MyModule()])

# Resolve dependencies
client = injector_instance.get(Client)

# Use the client
print(client.service.name)  # Output: MyService
