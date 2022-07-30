package Controller.ControlLogin;
import Controller.ControlLibrarian.LibrarianAccountController;
import Controller.ControlLibrarian.LibrarianAccountControllerService;
import Controller.ControlStudent.StudentAccountController;
import Controller.ControlStudent.StudentAccountControllerService;
import DataStorage.DataSource;
import DataStorage.DataSourceService;
import Model.LibrarianAccountModel;
import Model.StudentAccountModel;
import View.ViewLibrarian.LibrarianAccountView;
import View.ViewLibrarian.LibrarianMenuView;
import View.ViewLibrarian.PrintLibrarianInfoView;
import View.ViewStudent.PrintStudentInfoView;
import View.ViewStudent.StudentAccountView;
import View.ViewStudent.StudentMenuView;

public class LoginUtility {
    private DataSourceService dataSource= DataSource.getInstance();
    public boolean containsLibrarianAccount(String userName){
        return dataSource.containsLibrarian(userName);
    }
    public LibrarianAccountModel getLibrarianModel(String userName){
        return dataSource.getLibrarian(userName);
    }
    public boolean containsStudentAccount(String userName){
        return dataSource.containsStudent(userName);
    }
    public StudentAccountModel getStudentModel(String userName){
        return dataSource.getStudent(userName);
    }
    public StudentAccountControllerService getStudentAccountController(StudentAccountModel studentAccountModel){
        return new StudentAccountController(studentAccountModel,new StudentAccountView(),new StudentMenuView(),new PrintStudentInfoView());
    }
    public LibrarianAccountControllerService getLibrarianAccountController(LibrarianAccountModel librarianAccountModel){
        return new LibrarianAccountController(librarianAccountModel,new LibrarianAccountView(),new LibrarianMenuView(),new PrintLibrarianInfoView());
    }
    public void setIdOfLibrarian(int userId, String userName) {
        dataSource.setLibrarianId(userId,userName);
    }

    public void setIdOfStudent(int userId, String userName) {
        dataSource.setStudentId(userId,userName);
    }
}
