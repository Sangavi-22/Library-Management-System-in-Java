package DataStorage;
import FileOperations.FileHandler;
import FileOperations.FileHandlingService;
import Model.*;
import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;

public class DataSource implements DataSourceService{
    private static DataSource dataSource=null;
    private FileHandlingService fileHandler=new FileHandler();
    private DataSource() throws IOException {
        //Constructor of DataStorage.DataSource class
    }
    public static DataSource getInstance(){
        if( dataSource==null) {
            try {
                dataSource =new DataSource();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
        return dataSource;
    }
    public ArrayList<Integer> getBooks(){
        return fileHandler.readBooksIds();
    }
    public void addBookDetails(int id,BookDetailsModel bookDetailsModel){
        fileHandler.addBookDetailsToFile(id,bookDetailsModel);
    }
    public boolean containsBookDetails(int id) {
        return fileHandler.containsDetailsOfBook(id);
    }
    public BookDetailsModel getBookDetails(int id) {
        return fileHandler.readBookDetails(id);
    }
    public ArrayList<Integer> getBookId(String bookName) {
        return fileHandler.readId(bookName);
    }
    public void removeBookDetails(int id){
        fileHandler.removeBookDetailsFromFile(id);
    }
    public void addBookDate(int id, BookDatesModel bookDatesModel){
        fileHandler.addBookDatesToFile(id,bookDatesModel);
    }
    public void removeBookDate(int id){
        fileHandler.removeBookDatesFromFile(id);
    }
    public void addBookAuthors(int id,BookAuthorModel bookAuthorModel){
        fileHandler.addBookAuthorsToFile(id,bookAuthorModel);
    }
    public ArrayList<Integer> getBookIdWithAuthor(String authorName) {
        return fileHandler.getBookIdWithAuthorName(authorName);
    }
    public void removeBookAuthors(int id){
        fileHandler.removeBookAuthorsFromFile(id);
    }
    public void addBookPages(int id,BookPagesModel bookPagesModel){
        fileHandler.addBookPagesToFile(id,bookPagesModel);
    }
    public BookPagesModel getBookPages(int id) {
        return fileHandler.readBookPages(id);
    }
    public BookAuthorModel getBookAuthors(int id) {
        return fileHandler.readBookAuthors(id);
    }
    public void removeBookPages(int id){
        fileHandler.removeBookPagesFromFile(id);
    }
    public void addBookToLibrary(int id,int count) {
        fileHandler.addBookToFile(id,count);
    }
    public void updateBookCount(int id,int action) {
        fileHandler.changeBookCount(id,action);
    }
    public int bookAvailable(int id){
        return fileHandler.readBookCount(id);
    }
    public void addBorrower(int id,StudentAccountModel studentAccountModel){
        fileHandler.addBookBorrowersToFile(id,studentAccountModel);
    }
    public void removeBorrower(int id){
        fileHandler.removeBookBorrowersFromFile(id);
    }
    public HashMap<Integer, StudentAccountModel> getBorrowers(){
        return fileHandler.getBorrowerDetails();
    }
    public int getBorrowedCount(StudentAccountModel studentAccountModel){
        return fileHandler.readBorrowedBooksCount(studentAccountModel);
    }
    public void addStudent(String userName,StudentAccountModel studentAccountModel){
        fileHandler.addStudentDetails(userName,studentAccountModel);
    }
    public void addLibrarian(String userName,LibrarianAccountModel librarianAccountModel){
        fileHandler.addLibrarianDetails(userName,librarianAccountModel);
    }
    public void removeStudent(String userName){
        fileHandler.removeStudentDetails(userName);
    }
    public void removeLibrarian(String userName){
        fileHandler.removeLibrarianDetails(userName);
    }
    public boolean containsStudent(String userName){
        return fileHandler.containsStudentDetails(userName);
    }
    public boolean containsLibrarian(String userName){
        return fileHandler.containsLibrarianDetails(userName);
    }
    public LibrarianAccountModel getLibrarian(String userName){
        return fileHandler.getLibrarianDetails(userName);
    }
    public StudentAccountModel getStudent(String userName){
        return fileHandler.getStudentDetails(userName);
    }
    public int getLastBookId(){
        return fileHandler.readLastBookId();
    }
    public int getLastBookLocation(){
        return fileHandler.readLibraryLastLocation();
    }
    public void setStudentId(int id,String userName){
        fileHandler.writeStudentId(id,userName);
    }
    public int getIdForStudent(){
        return fileHandler.readLastStudentId();
    }
    public void setLibrarianId(int id,String userName){
       fileHandler.writeLibrarianId(id,userName);
    }
    public int getIdForLibrarian(){
        return fileHandler.readLastLibrarianId();
    }
    public void removeLibrarianId(String userName){
        fileHandler.removeLibrarian(userName);
    }
    public void removeStudentId(String userName){
        fileHandler.removeStudent(userName);
    }
}
