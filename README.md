# Base class: Hero
class Hero:
    def __init__(self, name, real_name, power, secret_identity=True):
        self.name = name  # Public attribute
        self._real_name = real_name  # Protected attribute
        self.__power = power  # Private attribute
        self.secret_identity = secret_identity  # Public attribute

    # Getter method to access private attribute
    def get_power(self):
        return self.__power

    # Setter method to change private attribute
    def set_power(self, new_power):
        self.__power = new_power

    # Method to reveal hero information
    def reveal_identity(self):
        if self.secret_identity:
            return f"{self.name} is {self._real_name}, keeping their identity a secret!"
        else:
            return f"{self.name} is {self._real_name}, no secret here!"

    # Method for hero to use their power
    def use_power(self):
        return f"{self.name} is using {self.__power}!"

# Derived class: Superhero
class Superhero(Hero):
    def __init__(self, name, real_name, power, secret_identity=True, team=None):
        # Inheriting from Hero class
        super().__init__(name, real_name, power, secret_identity)
        self.team = team if team else "Solo"  # Additional attribute for team

    # Overriding the method to customize the hero reveal
    def reveal_identity(self):
        return f"{self.name}, also known as {self._real_name}, is a member of the {self.team} team!"

    # Method to display superhero's full details
    def superhero_details(self):
        return f"Superhero: {self.name}\nReal Name: {self._real_name}\nPower: {self.__power}\nTeam: {self.team}"

# Derived class: Villain
class Villain(Hero):
    def __init__(self, name, real_name, power, secret_identity=True, evil_plan="World domination"):
        super().__init__(name, real_name, power, secret_identity)
        self.evil_plan = evil_plan  # Unique attribute for Villain

    # Overriding the method to show villain's evil plan
    def reveal_identity(self):
        return f"{self.name} is {self._real_name} and their evil plan is: {self.evil_plan}!"

    # Method for villain to execute their evil plan
    def execute_plan(self):
        return f"{self.name} is executing their evil plan: {self.evil_plan}!"

# Instantiate Superhero and Villain objects
superhero1 = Superhero("Captain Marvel", "Carol Danvers", "Super Strength", team="Avengers")
villain1 = Villain("Thanos", "Thanos", "Infinity Gauntlet", evil_plan="Collect all Infinity Stones")

# Demonstrating methods and polymorphism
print(superhero1.reveal_identity())  # Polymorphism: Overriden method
print(superhero1.use_power())
print(superhero1.superhero_details())

print(villain1.reveal_identity())  # Polymorphism: Overriden method
print(villain1.execute_plan())
