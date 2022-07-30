package Controller.ControlStudent;
import DataStorage.DataSource;
import DataStorage.DataSourceService;
import Model.StudentAccountModel;
import Payment.PaymentOperation;
import View.ViewStudent.PrintStudentInfoViewService;
import View.ViewStudent.StudentAccountViewService;
import View.ViewStudent.StudentMenuViewService;

public class StudentAccountController implements StudentAccountControllerService {
    private final StudentAccountModel model;
    private final StudentAccountViewService view;
    private final StudentMenuViewService studentMenuView;
    private final PrintStudentInfoViewService printStudentInfoView;
    private final static DataSourceService dataSource= DataSource.getInstance();
    public StudentAccountController(StudentAccountModel model, StudentAccountViewService view,StudentMenuViewService studentMenuView,PrintStudentInfoViewService printStudentInfoView){
        this.model=model;
        this.view=view;
        this.studentMenuView=studentMenuView;
        this.printStudentInfoView=printStudentInfoView;
    }
    public void setInputs(String userName,String password,int userId){
        this.setUserName(userName);
        this.setPassword(password);
        this.setStudentId(userId);
        this.view.inputStudentDetails(this);
        this.addStudentToDataSource();
    }
    public void addStudentToDataSource(){
        dataSource.addStudent(this.getUserName(),this.model);
    }
    public void menu(){
        this.studentMenuView.setController(this);
        this.studentMenuView.studentMenu();
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
    public void setStudentId(int id){
        this.model.setId(id);
    }
    public int getStudentId(){
       return this.model.getId();
    }
    public void setBorrowedCount(){
        this.model.setBorrowedCount();
    }
    public void updateBorrowedCount(){
        this.model.updateBorrowedCount();
    }
    public int getBorrowedCount(){
        return this.model.getBorrowedCount();
    }
    public void payFineThroughCard(PaymentOperation payment,String cardNumber){
        payment.transferAmount(cardNumber);
    }
    public void payFineThroughGooglePay(PaymentOperation payment,String googlePayId){
        payment.transferAmount(googlePayId);
    }
    public StudentAccountModel getStudentModel(){
        return this.model;
    }
    public void updateView(){
        this.printStudentInfoView.printStudentDetails(this.getName(),this.getEmail(),this.getMobileNum(),this.getStudentId());
    }
}
