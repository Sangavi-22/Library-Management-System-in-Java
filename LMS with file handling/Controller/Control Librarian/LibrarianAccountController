package Controller.ControlLibrarian;
import DataStorage.DataSource;
import DataStorage.DataSourceService;
import Model.LibrarianAccountModel;
import View.ViewLibrarian.LibrarianAccountViewService;
import View.ViewLibrarian.LibrarianMenuViewService;
import View.ViewLibrarian.PrintLibrarianInfoViewService;
public class LibrarianAccountController implements LibrarianAccountControllerService {
    private final LibrarianAccountModel model;
    private final LibrarianAccountViewService view;
    private final LibrarianMenuViewService librarianMenuView;
    private final PrintLibrarianInfoViewService printLibrarianInfoView;
    private final static DataSourceService dataSource= DataSource.getInstance();
    public LibrarianAccountController(LibrarianAccountModel model, LibrarianAccountViewService view,LibrarianMenuViewService librarianMenuView,PrintLibrarianInfoViewService printLibrarianInfoView){
        this.model=model;
        this.view=view;
        this.librarianMenuView=librarianMenuView;
        this.printLibrarianInfoView=printLibrarianInfoView;
    }
    public void setInputs(String userName,String password,int userId){
        this.setUserName(userName);
        this.setPassword(password);
        this.setLibrarianId(userId);
        this.view.inputLibrarianDetails(this);
        this.addLibrarianToDataSource();
    }
    public void addLibrarianToDataSource(){
        dataSource.addLibrarian(this.getUserName(),this.model);
    }
    public void menu(){
        this.librarianMenuView.setController(this);
        this.librarianMenuView.librarianMenu();
    }
    public void setName(String name){
        this.model.setName(name);
    }
    public String getName(){
        return this.model.getName();
    }
    public void setEmail(String email){
        this.model.setEmail(email);
    }
    public String getEmail(){
        return this.model.getEmail();
    }
    public void setMobileNum(long mobileNum){
        this.model.setMobileNum(mobileNum);
    }
    public long getMobileNum(){
        return this.model.getMobileNum();
    }
    public void setUserName(String userName){
        this.model.setUserName(userName);
    }
    public String getUserName(){
        return this.model.getUserName();
    }
    public void setPassword(String password){
        this.model.setPassword(password);
    }
    public String getPassword(){
        return this.model.getPassword();
    }
    public void setLibrarianId(int id){
        this.model.setId(id);
    }
    public int getLibrarianId(){
       return this.model.getId();
    }
    public void updateView(){
        printLibrarianInfoView.printLibrarianDetails(this.getName(),this.getEmail(),this.getMobileNum(),this.getLibrarianId());
    }
}
