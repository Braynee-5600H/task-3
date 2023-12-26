# task-3
contact book for a user



## task 3: contact book

contacts = []


def add_contact(name, phone, email, address):
    contact = {"Name": name, "Phone": phone, "Email": email, "Address": address}
    contacts.append(contact)
    print("Contact added successfully.")


def view_contacts():
    if not contacts:
        print("No contacts available.")
    else:
        print("Contact List:")
        for contact in contacts:
            print(f"Name: {contact['Name']}, Phone: {contact['Phone']}")


def search_contact(keyword):
    results = [contact for contact in contacts if
               keyword.lower() in contact['Name'].lower() or keyword in contact['Phone']]
    if not results:
        print("No matching contacts found.")
    else:
        print("Matching Contacts:")
        for result in results:
            print(f"Name: {result['Name']}, Phone: {result['Phone']}")


def update_contact(old_phone, new_contact):
    for i, contact in enumerate(contacts):
        if contact['Phone'] == old_phone:
            contacts[i] = new_contact
            print("Contact updated successfully.")
            return
    print("Contact not found.")


def delete_contact(phone):
    global contacts
    contacts = [contact for contact in contacts if contact['Phone'] != phone]
    print("Contact deleted successfully.")


while True:
    print("\nContact Management System")
    print("1. Add Contact")
    print("2. View Contact List")
    print("3. Search Contact")
    print("4. Update Contact")
    print("5. Delete Contact")
    print("6. Exit")

    choice = input("Enter your choice (1-6): ")

    if choice == "1":
        name = input("Enter name: ")
        phone = input("Enter phone number: ")
        email = input("Enter email: ")
        address = input("Enter address: ")
        add_contact(name, phone, email, address)

    elif choice == "2":
        view_contacts()

    elif choice == "3":
        keyword = input("Enter name or phone number to search: ")
        search_contact(keyword)

    elif choice == "4":
        old_phone = input("Enter the phone number of the contact to update: ")
        name = input("Enter updated name: ")
        phone = input("Enter updated phone number: ")
        email = input("Enter updated email: ")
        address = input("Enter updated address: ")
        updated_contact = {"Name": name, "Phone": phone, "Email": email, "Address": address}
        update_contact(old_phone, updated_contact)

    elif choice == "5":
        phone = input("Enter the phone number of the contact to delete: ")
        delete_contact(phone)

    elif choice == "6":
        print("Exiting Contact Management System.")
        break

    else:
        print("Invalid choice. Please enter a number between 1 and 6.")

