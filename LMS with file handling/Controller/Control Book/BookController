package Controller.ControlBook;
import Model.BookAuthorModel;
import Model.BookDatesModel;
import Model.BookDetailsModel;
import Model.BookPagesModel;
import View.ViewBook.BookViewService;
import View.ViewBook.PrintBookInfoViewService;
import java.time.LocalDate;
import java.time.temporal.ChronoUnit;
import java.util.ArrayList;
public class BookController implements BookControllerService {
    private long difference;
    private final BookDetailsModel bookDetailsModel;
    private final BookDatesModel bookDatesModel;
    private final BookPagesModel bookPagesModel;
    private final BookAuthorModel bookAuthorModel;
    private final BookViewService bookView;
    private final PrintBookInfoViewService printBookInfoView;
    public BookController(BookDetailsModel bookDetailsModel, BookDatesModel bookDatesModel, BookPagesModel bookPagesModel, BookAuthorModel bookAuthorModel, BookViewService bookView, PrintBookInfoViewService printBookInfoView){
        this.bookDetailsModel=bookDetailsModel;
        this.bookDatesModel=bookDatesModel;
        this.bookPagesModel=bookPagesModel;
        this.bookAuthorModel=bookAuthorModel;
        this.bookView=bookView;
        this.printBookInfoView=printBookInfoView;
    }
    public void setInputs(){
        this.bookView.inputBookDetails(this);
    }
    public void setBookId(int bookId) {
        this.bookDetailsModel.setBookId(bookId);
    }
    public int getBookId() {
        return this.bookDetailsModel.getBookId();
    }
    public void setBookLocationId(int locationId){
        this.bookDetailsModel.setBookLocation(locationId);
    }
    public int getBookLocation(){
        return this.bookDetailsModel.getBookLocation();
    }
    public void setBookName(String bookName){
        this.bookDetailsModel.setBookName(bookName);
    }
    public String getBookName(){
        return this.bookDetailsModel.getBookName();
    }
    public void setPublicationName(String publicationName){
        this.bookDetailsModel.setPublicationName(publicationName);
    }
    public String getPublicationName(){
        return this.bookDetailsModel.getPublicationName();
    }
    public void setBookCost(int bookCost){
        this.bookDetailsModel.setBookCost(bookCost);
    }
    public int getBookCost(){
        return this.bookDetailsModel.getBookCost();
    }
    public void setBookCount(){
        this.bookDetailsModel.setBookCount();
    }
    public int getBookCount(){
        return this.bookDetailsModel.getBookCount();
    }
    public void updateBookCount(){
        this.bookDetailsModel.updateBookCount();
    }
    public void setNoOfPages(int pages){
        this.bookPagesModel.setNoOfPages(pages);
    }
    public int getNoOfPages(){
        return this.bookPagesModel.getNoOfPages();
    }
    public void setPageLayout(String pageLayout){
        this.bookPagesModel.setPageLayout(pageLayout);
    }
    public String getPageLayout(){
        return this.bookPagesModel.getPageLayout();
    }
    public void addAuthorName(String authorName){
        this.bookAuthorModel.addAuthorName(authorName);
    }
    public ArrayList<String> getAuthorsName(){
        return this.bookAuthorModel.getAuthorsName();
    }
    public void setBookIssueDate(){
        this.bookDatesModel.setBookIssueDate();
    }
    public LocalDate getIssueDate(){
        return this.bookDatesModel.getIssueDate();
    }
    public void setBookDueDate(){
        this.bookDatesModel.setBookDueDate();
    }
    public LocalDate getBookDueDate(){
        return this.bookDatesModel.getBookDueDate();
    }
    public void setBookReturnedDateForReturn() {
        this.bookDatesModel.setBookReturnedDateForReturn();
    }
    public void setBookReturnedDateForRenew() {
        this.bookDatesModel.setBookReturnedDateForRenew();
    }
    public LocalDate getBookReturnedDate(){
        return this.bookDatesModel.getBookReturnedDate();
    }
    public long hasExpired(){
        if(this.getBookDueDate()!= null && this.getBookReturnedDate()!= null) {
            if (this.getBookDueDate().isBefore(this.getBookReturnedDate())) {
                difference= ChronoUnit.DAYS.between(this.getBookReturnedDate(),this.getBookDueDate());
            }
        }
        return difference;
    }
    public void updateView(){
        printBookInfoView.printBookDetails(this.getBookId(),this.getBookName(),this.getPublicationName(),
                this.getBookCost(),this.getNoOfPages(),this.getPageLayout(),this.getAuthorsName(),this.getBookLocation());
    }
    public void printDates(){
        printBookInfoView.printDates(this.getIssueDate(),this.getBookDueDate(),this.getBookId());
    }
    public void printBookId(){
        printBookInfoView.printBookId(this.getBookId());
    }
}
