Here’s a simple Python-based Airport Management System that you can use as a starting point and upload to your GitHub repository. It includes basic features like:

Adding flights

Viewing flight schedules

Booking tickets

Viewing passengers list



---

Airport Management System – Python Code

# airport_management.py

class Flight:
    def __init__(self, flight_no, origin, destination, time):
        self.flight_no = flight_no
        self.origin = origin
        self.destination = destination
        self.time = time
        self.passengers = []

    def book_ticket(self, passenger_name):
        self.passengers.append(passenger_name)
        print(f"Ticket booked for {passenger_name} on flight {self.flight_no}")

    def display_info(self):
        print(f"Flight: {self.flight_no} | {self.origin} -> {self.destination} at {self.time}")
        print(f"Passengers: {', '.join(self.passengers) if self.passengers else 'No passengers yet'}")


class AirportManagement:
    def __init__(self):
        self.flights = []

    def add_flight(self):
        flight_no = input("Flight Number: ")
        origin = input("Origin: ")
        destination = input("Destination: ")
        time = input("Time (e.g. 14:00): ")
        flight = Flight(flight_no, origin, destination, time)
        self.flights.append(flight)
        print("Flight added successfully.")

    def view_flights(self):
        if not self.flights:
            print("No flights available.")
            return
        for f in self.flights:
            f.display_info()

    def book_ticket(self):
        flight_no = input("Enter flight number to book ticket: ")
        name = input("Enter passenger name: ")
        for f in self.flights:
            if f.flight_no == flight_no:
                f.book_ticket(name)
                return
        print("Flight not found.")

    def run(self):
        while True:
            print("\n--- Airport Management System ---")
            print("1. Add Flight")
            print("2. View Flights")
            print("3. Book Ticket")
            print("4. Exit")
            choice = input("Select an option: ")

            if choice == '1':
                self.add_flight()
            elif choice == '2':
                self.view_flights()
            elif choice == '3':
                self.book_ticket()
            elif choice == '4':
                print("Exiting system.")
                break
            else:
                print("Invalid choice.")


if __name__ == "__main__":
    system = AirportManagement()
    system.run()
