# codsofttask03
Contact Book  
Contact Information: Store name, phone number, email, and address for each contact.
 Add Contact: Allow users to add new contacts with their details.
 View Contact List: Display a list of all saved contacts with names and phone numbers.
 Search Contact: Implement a search function to find contacts by name or phone number.
 Update Contact: Enable users to update contact details.
 Delete Contact: Provide an option to delete a contact.
 User Interface: Design a user-friendly interface for easy interaction.

code:
class Contact:
    def __init__(self, name, phone_number, email, address):
        self.name = name
        self.phone_number = phone_number
        self.email = email
        self.address = address
class ContactManager:
    def __init__(self):
        self.contacts = {}
    def add_contact(self, name, phone_number, email, address):
        if name not in self.contacts:
            self.contacts[name] = Contact(name, phone_number, email, address)
            print(f"Contact {name} added successfully.")
        else:
            print(f"Contact {name} already exists.")
    def view_contact_list(self):
        if not self.contacts:
            print("No contacts available.")
        else:
            for contact in self.contacts.values():
                print(f"Name: {contact.name}, Phone Number: {contact.phone_number}")
    def search_contact(self, query):
        results = [contact for contact in self.contacts.values() if query in contact.name or query in contact.phone_number]
        if not results:
            print("No contacts found.")
        else:
            for contact in results:
                print(f"Name: {contact.name}, Phone Number: {contact.phone_number}")
    def update_contact(self, name, phone_number=None, email=None, address=None):
        if name in self.contacts:
            if phone_number:
                self.contacts[name].phone_number = phone_number
            if email:
                self.contacts[name].email = email
            if address:
                self.contacts[name].address = address
            print(f"Contact {name} updated successfully.")
        else:
            print(f"Contact {name} not found.")
    def delete_contact(self, name):
        if name in self.contacts:
            del self.contacts[name]
            print(f"Contact {name} deleted successfully.")
        else:
            print(f"Contact {name} not found.")

def main():
    contact_manager = ContactManager()

    while True:
        print("\nContact Management System")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            name = input("Enter contact name: ")
            phone_number = input("Enter contact phone number: ")
            email = input("Enter contact email: ")
            address = input("Enter contact address: ")
            contact_manager.add_contact(name, phone_number, email, address)
        elif choice == "2":
            contact_manager.view_contact_list()
        elif choice == "3":
            query = input("Enter search query: ")
            contact_manager.search_contact(query)
        elif choice == "4":
            name = input("Enter contact name: ")
            phone_number = input("Enter new phone number (optional): ")
            email = input("Enter new email (optional): ")
            address = input("Enter new address (optional): ")
            contact_manager.update_contact(name, phone_number or None, email or None, address or None)
        elif choice == "5":
            name = input("Enter contact name: ")
            contact_manager.delete_contact(name)
        elif choice == "6":
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
