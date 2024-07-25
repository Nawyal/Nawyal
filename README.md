import random

class Duck:
    def __init__(self, name):
        self.name = name
        self.energy = 50
        self.hunger = 0
    
    def quack(self):
        print(f"{self.name} quacks!")
        self.energy -= 5
        self.hunger += 1
    
    def eat(self):
        print(f"{self.name} eats.")
        self.energy += 10
        self.hunger -= 3
    
    def rest(self):
        print(f"{self.name} rests.")
        self.energy += 5
        self.hunger += 1
    
    def status(self):
        print(f"{self.name}: Energy {self.energy}, Hunger {self.hunger}")

# Main game loop
def main():
    duck_name = input("Enter your duck's name: ")
    duck = Duck(duck_name)
    while duck.energy > 0:
        action = input("Enter an action (quack, eat, rest, status, exit): ").strip().lower()
        
        if action == 'quack':
            duck.quack()
        elif action == 'eat':
            duck.eat()
        elif action == 'rest':
            duck.rest()
        elif action == 'status':
            duck.status()
        elif action == 'exit':
            print("Exiting game.")
            break
        else:
            print("Invalid action. Try again.")
        
        # Duck gets hungry and loses energy over time
        duck.hunger += random.randint(1, 3)
        duck.energy -= random.randint(1, 5)
        
        if duck.hunger >= 10:
            print(f"{duck.name} is very hungry!")
        if duck.energy <= 0:
            print(f"{duck.name} is too tired to continue!")

if __name__ == "__main__":
    main()
