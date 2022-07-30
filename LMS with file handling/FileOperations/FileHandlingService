package FileOperations;
import Model.*;

import java.util.ArrayList;
import java.util.HashMap;
public interface FileHandlingService {
    void addBookDetailsToFile(int id, BookDetailsModel bookDetailsModel);
    void removeBookDetailsFromFile(int id);
    void addBookDatesToFile(int id, BookDatesModel bookDatesModel);
    void removeBookDatesFromFile(int id);
    void addBookAuthorsToFile(int id, BookAuthorModel bookAuthorModel);
    void removeBookAuthorsFromFile(int id);

    void addBookPagesToFile(int id, BookPagesModel bookPagesModel);

    void removeBookPagesFromFile(int id);

    void addBookBorrowersToFile(int id, StudentAccountModel studentAccountModel);

    void removeBookBorrowersFromFile(int id);

    HashMap<Integer, StudentAccountModel> getBorrowerDetails();

    void addStudentDetails(String userName, StudentAccountModel studentAccountModel);

    void addLibrarianDetails(String userName, LibrarianAccountModel librarianAccountModel);

    void removeStudentDetails(String userName);

    void removeLibrarianDetails(String userName);

    boolean containsStudentDetails(String userName);

    boolean containsLibrarianDetails(String userName);

    LibrarianAccountModel getLibrarianDetails(String userName);

    StudentAccountModel getStudentDetails(String userName);

    boolean containsDetailsOfBook(int id);

    void changeBookCount(int id, int action);

    void addBookToFile(int id, int count);

    BookPagesModel readBookPages(int id);

    BookDetailsModel readBookDetails(int id);

    ArrayList<Integer> readId(String bookName);

    ArrayList<Integer> getBookIdWithAuthorName(String authorName);

    int readBookCount(int id);

    int readBorrowedBooksCount(StudentAccountModel studentAccountModel);

    BookAuthorModel readBookAuthors(int id);

    ArrayList<Integer> readBooksIds();

    int readLastBookId();

    int readLibraryLastLocation();

    void writeStudentId(int id, String userName);

    int readLastStudentId();

    void writeLibrarianId(int id, String userName);

    int readLastLibrarianId();

    void removeLibrarian(String userName);

    void removeStudent(String userName);
}
