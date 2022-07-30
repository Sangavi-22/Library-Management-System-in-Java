package DataStorage;
import Model.*;

import java.util.ArrayList;
import java.util.HashMap;
public interface DataSourceService {
    void addBookDetails(int id, BookDetailsModel bookDetailsModel);

    void removeBookDetails(int id);

    void addBookDate(int id, BookDatesModel bookDatesModel);

    void removeBookDate(int id);

    void addBookAuthors(int id, BookAuthorModel bookAuthorModel);

    void removeBookAuthors(int id);

    void addBookPages(int id, BookPagesModel bookPagesModel);

    void removeBookPages(int id);

    void addBorrower(int id, StudentAccountModel studentAccountModel);

    void removeBorrower(int id);

    HashMap<Integer, StudentAccountModel> getBorrowers();

    void addStudent(String userName, StudentAccountModel studentAccountModel);

    void addLibrarian(String userName, LibrarianAccountModel librarianAccountModel);

    void removeStudent(String userName);

    void removeLibrarian(String userName);

    boolean containsStudent(String userName);

    boolean containsLibrarian(String userName);

    LibrarianAccountModel getLibrarian(String userName);

    StudentAccountModel getStudent(String userName);

    void addBookToLibrary(int bookId, int i);

    boolean containsBookDetails(int id);

    void updateBookCount(int id, int i);

    BookDetailsModel getBookDetails(int id);

    BookPagesModel getBookPages(int id);

    BookAuthorModel getBookAuthors(int id);

    ArrayList<Integer> getBookId(String book);

    ArrayList<Integer> getBookIdWithAuthor(String authorName);

    int bookAvailable(int id);

    int getBorrowedCount(StudentAccountModel studentAccountModel);

    ArrayList<Integer> getBooks();

    int getLastBookId();
    int getLastBookLocation();

    void setLibrarianId(int userId, String userName);

    void removeLibrarianId(String user);

    void removeStudentId(String user);

    void setStudentId(int userId, String userName);

    int getIdForStudent();

    int getIdForLibrarian();
}
