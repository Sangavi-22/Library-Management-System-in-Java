package FileOperations;
import Controller.ControlStudent.StudentAccountController;
import Controller.ControlStudent.StudentAccountControllerService;
import Model.*;
import View.ViewStudent.PrintStudentInfoView;
import View.ViewStudent.StudentAccountView;
import View.ViewStudent.StudentMenuView;
import java.io.*;
import java.util.ArrayList;
import java.util.HashMap;
public class FileHandler implements FileHandlingService {
    File LibrarianDetails=new File("/Users/sangavi-pt5468/Desktop/LMS/LibrarianDetails.txt");
    File LibrarianDetailsTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/LibrarianDetailsTemp.txt");
    File StudentDetails=new File("/Users/sangavi-pt5468/Desktop/LMS/StudentDetails.txt");
    File StudentDetailsTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/StudentDetailsTemp.txt");
    File BookDetails=new File("/Users/sangavi-pt5468/Desktop/LMS/BookDetails.txt");
    File BookDetailsTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/BookDetailsTemp.txt");
    File BookDates=new File("/Users/sangavi-pt5468/Desktop/LMS/BookDates.txt");
    File BookDatesTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/BookDatesTemp.txt");
    File BookAuthors = new File("/Users/sangavi-pt5468/Desktop/LMS/BookAuthors.txt");
    File BookAuthorsTemp = new File("/Users/sangavi-pt5468/Desktop/LMS/BookAuthorsTemp.txt");
    File BookPages=new File("/Users/sangavi-pt5468/Desktop/LMS/BookPages.txt");
    File BookPagesTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/BookPagesTemp.txt");
    File Borrowers=new File("/Users/sangavi-pt5468/Desktop/LMS/Borrowers.txt");
    File BorrowersTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/BorrowersTemp.txt");
    File LibraryBooks=new File("/Users/sangavi-pt5468/Desktop/LMS/LibraryBooks.txt");
    File LibraryBooksTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/LibraryBooksTemp.txt");
    File StudentId=new File("/Users/sangavi-pt5468/Desktop/LMS/StudentId.txt");
    File StudentIdTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/StudentIdTemp.txt");
    File LibrarianId=new File("/Users/sangavi-pt5468/Desktop/LMS/LibrarianId.txt");
    File LibrarianIdTemp=new File("/Users/sangavi-pt5468/Desktop/LMS/LibrarianIdTemp.txt");

    public void addBookDetailsToFile(int id, BookDetailsModel bookDetailsModel) {
        try{
            BufferedWriter bw = new BufferedWriter(new FileWriter(BookDetails,true));
            bw.write("bookId:"+String.valueOf(id)+", bookLocation:"+String.valueOf(bookDetailsModel.getBookLocation())+", bookName:" + bookDetailsModel.getBookName()+ ", publicationName:" +bookDetailsModel.getPublicationName()+", bookCost:" + bookDetailsModel.getBookCost()+"\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public boolean containsDetailsOfBook(int id){
        boolean found=false;
        try{
            String[] words;
            String sentence;
            BufferedReader br=new BufferedReader(new FileReader(BookDetails));
            while((sentence=br.readLine())!=null) {
                words=sentence.split(", ");
                if(words[0].split(":")[1].equals(String.valueOf(id))) {
                    found = true;
                    break;
                }
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return found;
        }
    }
    public BookDetailsModel readBookDetails(int id){
        BookDetailsModel bookDetailsModel=new BookDetailsModel();
        HashMap<String,String>details=new HashMap<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookDetails));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if(words[0].split(":")[1].equals(String.valueOf(id))){
                    for(String part:words) {
                        details.put(part.split(":")[0],part.split(":")[1]);
                    }
                }
            }
            br.close();
            bookDetailsModel.setBookId(Integer.parseInt(details.get("bookId")));
            bookDetailsModel.setBookLocation(Integer.parseInt(details.get("bookLocation")));
            bookDetailsModel.setBookName(details.get("bookName"));
            bookDetailsModel.setPublicationName(details.get("publicationName"));
            bookDetailsModel.setBookCost(Integer.parseInt(details.get("bookCost")));
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return bookDetailsModel;
        }
    }
    public ArrayList<Integer>readBooksIds(){
        ArrayList<Integer>ids=new ArrayList<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookDetails));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                ids.add(Integer.parseInt(words[0].split(":")[1]));
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally{
            return ids;
        }
    }
    public ArrayList<Integer> readId(String bookName){
        ArrayList<Integer>ids=new ArrayList<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookDetails));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if(words[2].split(":")[1].contains(bookName)) {
                   ids.add(Integer.parseInt(words[0].split(":")[1]));
                }
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally{
            return ids;
        }
    }
    public void removeBookDetailsFromFile(int id){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(BookDetails));
            BufferedWriter writer = new BufferedWriter(new FileWriter(BookDetailsTemp,true));
            String lineToRemove="bookId:"+id+", bookLocation:";
            String currentLine;
            while((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if(trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            BookDetailsTemp.renameTo(BookDetails);
            PrintWriter wr = new PrintWriter(BookDetailsTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }

    public void addBookDatesToFile(int id,BookDatesModel bookDatesModel){
        try {
            BufferedWriter bw = new BufferedWriter(new FileWriter(BookDates,true));
            bw.write("bookId:"+id+", issueDate:"+bookDatesModel.getIssueDate().toString()+", dueDate:"+bookDatesModel.getBookDueDate().toString()+"\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }

    }
    public void removeBookDatesFromFile(int id){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(BookDates));
            BufferedWriter writer = new BufferedWriter(new FileWriter(BookDatesTemp,true));
            String lineToRemove="bookId:"+id+", issueDate:";
            String currentLine;
            while((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if(trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            BookDatesTemp.renameTo(BookDates);
            PrintWriter wr = new PrintWriter(BookDatesTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public void addBookAuthorsToFile(int id,BookAuthorModel bookAuthorModel){
        try {
            ArrayList<String> bookAuthors = bookAuthorModel.getAuthorsName();
            BufferedWriter bw = new BufferedWriter(new FileWriter(BookAuthors, true));
            bw.write("bookId:" + id + ", authors:");
            for (String authorNames : bookAuthors) {
                bw.write(authorNames + ">");
            }
            bw.write("\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }

    }
    public ArrayList<Integer> getBookIdWithAuthorName(String author){
        ArrayList<Integer>ids=new ArrayList<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookAuthors));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                String[] text=words[1].split(":");
                for(String parts:text[1].split(">")){
                    if (parts.contains(author)) {
                        ids.add(Integer.parseInt(words[0].split(":")[1]));
                        break;
                    }
                }
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally{
            return ids;
        }
    }
    public BookAuthorModel readBookAuthors(int id){
        BookAuthorModel bookAuthorModel=new BookAuthorModel();
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookAuthors));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if(words[0].split(":")[1].equals(String.valueOf(id))){
                    String[] text=words[1].split(":");
                    for(String part:text[1].split(">")) {
                        bookAuthorModel.addAuthorName(part);
                    }
                }
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return bookAuthorModel;
        }
    }
    public void removeBookAuthorsFromFile(int id){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(BookAuthors));
            BufferedWriter writer = new BufferedWriter(new FileWriter(BookAuthorsTemp, true));
            String lineToRemove = "bookId:" + id + ", authors";
            String currentLine;
            while ((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if (trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            BookAuthorsTemp.renameTo(BookAuthors);
            PrintWriter wr = new PrintWriter(BookAuthorsTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public void addBookPagesToFile(int id,BookPagesModel bookPagesModel){
        try {
            BufferedWriter bw = new BufferedWriter(new FileWriter(BookPages, true));
            bw.write("bookId:" + id + ", noOfPages:" + bookPagesModel.getNoOfPages() + ", pageLayout:" + bookPagesModel.getPageLayout() + "\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public BookPagesModel readBookPages(int id){
        BookPagesModel bookPagesModel=new BookPagesModel();
        HashMap<String,String>details=new HashMap<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookPages));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if(words[0].split(":")[1].equals(String.valueOf(id))){
                    for(String part:words) {
                        details.put(part.split(":")[0],part.split(":")[1]);
                    }
                }
            }
            br.close();
            bookPagesModel.setNoOfPages(Integer.parseInt(details.get("noOfPages")));
            bookPagesModel.setPageLayout(details.get("pageLayout"));
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return bookPagesModel;
        }
    }
    public void removeBookPagesFromFile(int id){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(BookPages));
            BufferedWriter writer = new BufferedWriter(new FileWriter(BookPagesTemp, true));
            String lineToRemove = "bookId:" + id + ", noOfPages:";
            String currentLine;
            while ((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if (trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            BookPagesTemp.renameTo(BookPages);
            PrintWriter wr = new PrintWriter(BookPagesTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public void addBookToFile(int id,int count){
        try {
            BufferedWriter bw = new BufferedWriter(new FileWriter(LibraryBooks,true));
            bw.write("bookId:"+id+", bookCount:"+count+"\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public void changeBookCount(int id,int action){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(LibraryBooks));
            BufferedWriter writer = new BufferedWriter(new FileWriter(LibraryBooksTemp,true));
            String lineToRemove="bookId:"+id+", bookCount:";
            String currentLine;
            while((currentLine = reader.readLine()) != null) {
                int bookCount=Integer.parseInt(currentLine.split(", ")[1].split(":")[1])+action;
                String trimmedLine = currentLine.trim();
                if(trimmedLine.contains(lineToRemove))
                    writer.write("bookId:"+id+", bookCount:"+bookCount+"\n");
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            LibraryBooksTemp.renameTo(LibraryBooks);
            PrintWriter wr = new PrintWriter(LibraryBooksTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public int readBookCount(int id){
        int count=0;
        try {
            BufferedReader br = new BufferedReader(new FileReader(LibraryBooks));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if(words[0].split(":")[1].equals(String.valueOf(id))) {
                    count=Integer.parseInt(words[1].split(":")[1]);
                }
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally{
            return count;
        }
    }
    public void addBookBorrowersToFile(int id, StudentAccountModel studentAccountModel){
        try {
            BufferedWriter bw = new BufferedWriter(new FileWriter(Borrowers, true));
            bw.write("bookId:" + id +", userName:"+studentAccountModel.getUserName()+", password:"+studentAccountModel.getPassword()+"name:" + studentAccountModel.getName() + ", email:" + studentAccountModel.getEmail() + ", mobileNum:" + studentAccountModel.getMobileNum() + ", studentId:" + studentAccountModel.getId() +", borrowedCount:"+studentAccountModel.getBorrowedCount()+ "\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }

    }
    public int readBorrowedBooksCount(StudentAccountModel studentAccountModel){
        int count=0;
        try {
            BufferedReader br = new BufferedReader(new FileReader(Borrowers));
            String sentence ;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if (words[1].split(":")[1].equals(studentAccountModel.getUserName())) {
                    count++;
                }
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return count;
        }
    }
    public HashMap<Integer, StudentAccountModel> getBorrowerDetails(){
        HashMap<Integer, StudentAccountModel>borrowers=new HashMap<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(Borrowers));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                HashMap<String,String>details=new HashMap<>();
                String[] words = sentence.split(", ");
                for(String part:words) {
                    details.put(part.split(":")[0],part.split(":")[1]);
                }
                StudentAccountModel studentAccountModel=new StudentAccountModel();
                studentAccountModel.setUserName(details.get("userName"));
                studentAccountModel.setPassword(details.get("password"));
                studentAccountModel.setName(details.get("name"));
                studentAccountModel.setEmail(details.get("email"));
                studentAccountModel.setMobileNum(Long.parseLong(details.get("mobileNum")));
                studentAccountModel.setId(Integer.parseInt(details.get("studentId")));
                borrowers.put(Integer.parseInt(details.get("bookId")),studentAccountModel);
            }
            br.close();

        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return borrowers;
        }

    }
    public void removeBookBorrowersFromFile(int id) {
        try {
            BufferedReader reader = new BufferedReader(new FileReader(Borrowers));
            BufferedWriter writer = new BufferedWriter(new FileWriter(BorrowersTemp, true));
            String lineToRemove = "bookId:" + id + ", userName:";
            String currentLine;
            while ((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if (trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            BorrowersTemp.renameTo(Borrowers);
            PrintWriter wr = new PrintWriter(BorrowersTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public void addLibrarianDetails(String userName,LibrarianAccountModel librarianAccountModel){
        try {
            BufferedWriter bw = new BufferedWriter(new FileWriter(LibrarianDetails, true));
            bw.write("userName:" + userName + ", password:" + librarianAccountModel.getPassword() + ", name:" + librarianAccountModel.getName() + ", email:" + librarianAccountModel.getEmail() + ", mobileNum:" + librarianAccountModel.getMobileNum()
                    + ", librarianId:" + librarianAccountModel.getId() + "\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public boolean containsLibrarianDetails(String userName){
        boolean found=false;
        try {
            BufferedReader br = new BufferedReader(new FileReader(LibrarianDetails));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                HashMap<String,String>details=new HashMap<>();
                String[] words = sentence.split(", ");
                for(String part:words) {
                    details.put(part.split(":")[0],part.split(":")[1]);
                }
                if(details.get("userName").equals(userName)) {
                    found=true;
                    break;
                }
            }
            br.close();

        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return found;
        }
    }
    public LibrarianAccountModel getLibrarianDetails(String userName){
        LibrarianAccountModel librarianAccountModel=new LibrarianAccountModel();
        HashMap<String,String>details=new HashMap<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(LibrarianDetails));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if(words[0].split(":")[1].equals(userName)){
                    for(String part:words) {
                        details.put(part.split(":")[0],part.split(":")[1]);
                    }
                }
            }
            br.close();
            librarianAccountModel.setUserName(details.get("userName"));
            librarianAccountModel.setPassword(details.get("password"));
            librarianAccountModel.setName(details.get("name"));
            librarianAccountModel.setEmail(details.get("email"));
            librarianAccountModel.setMobileNum(Long.parseLong(details.get("mobileNum")));
            librarianAccountModel.setId(Integer.parseInt(details.get("librarianId")));
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return librarianAccountModel;
        }

    }
    public void removeLibrarianDetails(String userName){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(LibrarianDetails));
            BufferedWriter writer = new BufferedWriter(new FileWriter(LibrarianDetailsTemp,true));
            String lineToRemove="userName:" + userName;
            String currentLine;
            while((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if(trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            LibrarianDetailsTemp.renameTo(LibrarianDetails);
            PrintWriter wr = new PrintWriter(LibrarianDetailsTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }

    }
    public void addStudentDetails(String userName,StudentAccountModel studentAccountModel){
        try {
            BufferedWriter bw = new BufferedWriter(new FileWriter(StudentDetails, true));
            StudentAccountControllerService studentAccountController = new StudentAccountController(studentAccountModel, new StudentAccountView(), new StudentMenuView(), new PrintStudentInfoView());
            bw.write("userName:" + userName + ", password:" + studentAccountController.getPassword() + ", name:" + studentAccountController.getName() + ", email:" + studentAccountController.getEmail() + ", mobileNum:" + studentAccountController.getMobileNum()
                    + ", studentId:" + studentAccountController.getStudentId() + "\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public boolean containsStudentDetails(String userName){
        boolean found=false;
        try {
            BufferedReader br = new BufferedReader(new FileReader(StudentDetails));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                HashMap<String,String>details=new HashMap<>();
                String[] words = sentence.split(", ");
                for(String part:words) {
                    details.put(part.split(":")[0],part.split(":")[1]);
                }
                if(details.get("userName").equals(userName)) {
                    found=true;
                    break;
                }
            }
            br.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {

            return found;
        }

    }
    public StudentAccountModel getStudentDetails(String userName)
    {
        StudentAccountModel studentAccountModel=new StudentAccountModel();
        HashMap<String,String>details=new HashMap<>();
        try {
            BufferedReader br = new BufferedReader(new FileReader(StudentDetails));
            String sentence;
            while ((sentence = br.readLine()) != null) {
                String[] words = sentence.split(", ");
                if(words[0].split(":")[1].equals(userName)){
                    for(String part:words) {
                        details.put(part.split(":")[0],part.split(":")[1]);
                    }
                }
            }
            br.close();
            studentAccountModel.setUserName(details.get("userName"));
            studentAccountModel.setPassword(details.get("password"));
            studentAccountModel.setName(details.get("name"));
            studentAccountModel.setEmail(details.get("email"));
            studentAccountModel.setMobileNum(Long.parseLong(details.get("mobileNum")));
            studentAccountModel.setId(Integer.parseInt(details.get("studentId")));
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
        finally {
            return studentAccountModel;
        }


    }
    public void removeStudentDetails(String userName){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(StudentDetails));
            BufferedWriter writer = new BufferedWriter(new FileWriter(StudentDetailsTemp,true));
            String lineToRemove="userName:" + userName;
            String currentLine;
            while((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if(trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            StudentDetailsTemp.renameTo(StudentDetails);
            PrintWriter wr = new PrintWriter(StudentDetailsTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
            throw new RuntimeException(e);
        }
    }
    public int readLastBookId(){
        int id=0;
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookDetails));
            String sentence;
            while ((sentence =br.readLine()) != null) {
                String[] words=sentence.split(", ");
                id=Integer.parseInt(words[0].split(":")[1]);
            }
            br.close();
        }
        catch(IOException e) {
        }
        finally {
            return id;
        }
    }
    public int readLibraryLastLocation(){
        int id=0;
        try {
            BufferedReader br = new BufferedReader(new FileReader(BookDetails));
            String sentence;
            while ((sentence =br.readLine()) != null) {
                String[] words=sentence.split(", ");
                id=Integer.parseInt(words[1].split(":")[1]);
            }
            br.close();
        }
        catch(IOException e) {
        }
        finally {
            return id;
        }
    }
    public void writeStudentId(int id,String userName){
        try {
            System.out.println(id);
            BufferedWriter bw = new BufferedWriter(new FileWriter(StudentId,true));
            bw.write("StudentId:"+id+", userName:"+userName+"\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e){
        }
    }
    public int readLastStudentId(){
        String sentence="";
        int id=1000;
        try{
            String[] words={};
            BufferedReader br=new BufferedReader(new FileReader(StudentId));
            while(br.ready()) {
                sentence=br.readLine();
                words=sentence.split(", ");
            }
            id=Integer.parseInt(words[0].split(":")[1]);
            br.close();
        }
        catch(IOException e) {
        }
        finally {
            return id;
        }
    }
    public boolean containsStudent(String userName){
        boolean found=false;
        try{
            String[] words={};
            String sentence="";
            BufferedReader br=new BufferedReader(new FileReader(StudentId));
            while((sentence=br.readLine())!=null) {
                words=sentence.split(", ");
                if(words[1].split(":")[1].equals(userName)) {
                    found = true;
                    break;
                }
            }
            br.close();
        }
        catch(IOException e) {
        }
        finally {
            return found;
        }
    }
    public void removeStudent(String userName){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(StudentId));
            BufferedWriter writer = new BufferedWriter(new FileWriter(StudentIdTemp,true));
            String lineToRemove=", userName:"+userName;
            String currentLine;
            while((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if(trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            StudentIdTemp.renameTo(StudentId);
            PrintWriter wr = new PrintWriter(StudentIdTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
        }
    }
    public void writeLibrarianId(int id,String userName){
        try {
            System.out.println(id);
            BufferedWriter bw = new BufferedWriter(new FileWriter(LibrarianId,true));
            bw.write("LibrarianId:"+id+", userName:"+userName+"\n");
            bw.flush();
            bw.close();
        }
        catch(IOException e){
        }
    }
    public int readLastLibrarianId(){
        String sentence="";
        int id=0;
        try{
            String[] words={};
            BufferedReader br=new BufferedReader(new FileReader(LibrarianId));
            while(br.ready()) {
                sentence=br.readLine();
                words=sentence.split(", ");
            }
            id=Integer.parseInt(words[0].split(":")[1]);
            br.close();
        }
        catch(IOException e) {
        }
        finally {
            return id;
        }
    }
    public boolean containsLibrarian(String userName){
        boolean found=false;
        try{
            String[] words={};
            String sentence="";
            BufferedReader br=new BufferedReader(new FileReader(LibrarianId));
            while((sentence=br.readLine())!=null) {
                words=sentence.split(", ");
                if(words[1].split(":")[1].equals(userName)) {
                    found = true;
                    break;
                }
            }
            br.close();
        }
        catch(IOException e) {
        }
        finally {
            return found;
        }
    }
    public void removeLibrarian(String userName){
        try {
            BufferedReader reader = new BufferedReader(new FileReader(LibrarianId));
            BufferedWriter writer = new BufferedWriter(new FileWriter(LibrarianIdTemp,true));
            String lineToRemove=", userName:"+userName;
            String currentLine;
            while((currentLine = reader.readLine()) != null) {
                String trimmedLine = currentLine.trim();
                if(trimmedLine.contains(lineToRemove))
                    continue;
                writer.write(currentLine + System.getProperty("line.separator"));
            }
            writer.flush();
            writer.close();
            reader.close();
            LibrarianIdTemp.renameTo(LibrarianId);
            PrintWriter wr = new PrintWriter(LibrarianIdTemp);
            wr.print("");
            wr.flush();
            wr.close();
        }
        catch(IOException e) {
        }
    }



}
