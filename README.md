class Book:
    def __str__(self):
        return f"'{self.title}' by {self.author} (Genre: {self.genre}) - {'Available 🙂' if self.available else 'Not Available 🙁'}"

# Global variables to manage the library
MAX_BOOKS = 10
books = []

class User:
    def __init__(self):
        return f"'{self.register} - {'Succesful'}"
    users = []

def add_book(title, author, genre):
    if len(books) >= MAX_BOOKS:
        print("Library is full. Cannot add more books.")
        return
    book = Book()
    book.title = title
    book.author = author
    book.genre = genre
    book.available = True
    books.append(book)
    print(f"Added: {book}")


def update_book(old_title, new_title=None, new_author=None, new_genre=None):
    for book in books:
        if book.title == old_title:
            if new_title:
                book.title = new_title
            if new_author:
                book.author = new_author
            if new_genre:
                book.genre = new_genre
            print(f"Updated: {book}")
            return
    print("Book not found.")


def delete_book(title):
    for book in books:
        if book.title == title:
            books.remove(book)
            print(f"Deleted: {book}")
            return
    print("Book not found.")


def borrow_book(title):
    for book in books:
        if book.title == title:
            if book.available:
                book.available = False
                print(f"You borrowed: {book}")
            else:
                print("Book is not available.")
            return
    print("Book not found.")


def return_book(title):
    for book in books:
        if book.title == title:
            book.available = True
            print(f"You returned: {book}")
            return
    print("Book not found.")


def search_books(query):
    results = [book for book in books if query.lower() in book.title.lower() or
               query.lower() in book.author.lower() or
               query.lower() in book.genre.lower()]
    if results:
        for book in results:
            print(book)
    else:
        print("No books found.")


def list_books():
    if books:
        for book in books:
            print(book)
    else:
        print("No books in the library.")




def main(register):
    while True:
        register = input("Enter Username To Register: ")
        register.user = register
        register.available = True
        users = users.append(register)
        print(f"Registered: {register}" )
        username = input("Enter username: ")
        if username == users:
            print("\nLibrary Management System")
        else:
            print("User Not registered")
            if username != users:
                return
        print("1. Add Book")
        print("2. Update Book")
        print("3. Delete Book")
        print("4. Borrow Book")
        print("5. Return Book")
        print("6. Search Books")
        print("7. List Books")
        print("8. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            title = input("Enter book title: ")
            author = input("Enter book author: ")
            genre = input("Enter book genre: ")
            add_book(title, author, genre)
        elif choice == "2":
            old_title = input("Enter the title of the book to update: ")
            new_title = input("Enter new title (leave blank to keep current): ")
            new_author = input("Enter new author (leave blank to keep current): ")
            new_genre = input("Enter new genre (leave blank to keep current): ")
            update_book(old_title, new_title or None, new_author or None, new_genre or None)
        elif choice == "3":
            title = input("Enter the title of the book to delete: ")
            delete_book(title)
        elif choice == "4":
            title = input("Enter the title of the book to borrow: ")
            borrow_book(title)
        elif choice == "5":
            title = input("Enter the title of the book to return: ")
            return_book(title)
        elif choice == "6":
            query = input("Enter title, author, or genre to search: ")
            search_books(query)
        elif choice == "7":
            list_books()
        elif choice == "8":
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")


if _name_ == "_main_":
    main()
