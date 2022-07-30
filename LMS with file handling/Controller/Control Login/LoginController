package Controller.ControlLogin;
import Model.LoginModel;
import View.ViewLogin.LoginViewService;
import DataStorage.DataSource;
import DataStorage.DataSourceService;
public class LoginController implements LoginControllerService {
    private final LoginModel loginModel;
    private final LoginViewService loginView;
    private DataSourceService dataSource= DataSource.getInstance();
    public LoginController(LoginModel loginModel, LoginViewService loginView) {
        this.loginModel = loginModel;
        this.loginView = loginView;
    }
    public void goToHomePage(){
        loginView.setLoginController(this);
        loginView.homePage();
    }
    public void removeUser(String user) {
        if(dataSource.containsLibrarian(user) && this.loginModel.getAccountName().equals(user)) {
            dataSource.removeLibrarian(user);
            dataSource.removeLibrarianId(user);
            this.loginView.removedUser("Librarian");
        }
        else if(dataSource.containsStudent(user)){
            dataSource.removeStudent(user);
            dataSource.removeStudentId(user);
            this.loginView.removedUser("Student");
        }
        else{
            this.loginView.removedUser("No User");
        }
    }
    public void setAccountName(String user){
        this.loginModel.setAccountName(user);
    }
    public String getAccountName(){
        return this.loginModel.getAccountName();
    }
    public void logOut() {
        loginView.loggedOut();
    }
}
