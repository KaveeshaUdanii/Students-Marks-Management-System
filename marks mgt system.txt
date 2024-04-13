import java.util.*;
public class Example {
    public static int[] Pmarks=new int[0];
    public static int[] Dmarks=new int[0];
    public static String [] idArray=new String[0];
    public static String [] namesArray=new String[0];
    public static int[] maxMarks=new int[0];
    
    public static void clearConsole(){ 
        try { 
            final String os = System.getProperty("os.name");
            if (os.contains("Windows")) { 
                new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
            } else { 
                System.out.print("\033[H\033[2J");
                System.out.flush();
            }
        }catch (final Exception e) {
            e.printStackTrace();
            // Handle any exceptions.
        }
    }
   
    
    public static int searchStuID(String stuid){
		for (int i = 0; i < idArray.length; i++){
			if(stuid.equalsIgnoreCase(idArray[i])){  //stId==stIdArray[i]-->Wrong
				return i;
			}
		}
		return -1;
    }
    
    
    
    public static void enterStudent(){
        do{
            System.out.println("---------------------------------------------------------------------------------------------");
            System.out.println("|                                 Add New Student                                            |");
            System.out.println("---------------------------------------------------------------------------------------------");

            Scanner input=new Scanner(System.in);
            System.out.print("Enter Student ID : "); 
            String stuid = input.nextLine();
            if (searchStuID(stuid)!=-1){
                System.out.println(stuid+" is already exists..");
                continue;
            }

            Scanner input1=new Scanner(System.in);
            System.out.print("Enter Student Name : ");
            String name= input1.nextLine();
                
            
            String []temp1=new String[idArray.length+1];
            for (int i = 0; i < idArray.length; i++) {
                        temp1[i]=idArray[i];
                    }
            temp1[temp1.length-1]=stuid;
            idArray=temp1;

            String []temp2=new String[namesArray.length+1];
            for (int i = 0; i < namesArray.length; i++) {
                        temp2[i]=namesArray[i];
                    }
            temp2[temp2.length-1]=name;
            namesArray=temp2;
            
            
            System.out.print("New student added successfully.");
            System.out.print("Do you want to add another (Y/N) : "); 
            String option=input.nextLine(); 
            if(option.equalsIgnoreCase("y")){
                clearConsole();
                continue;
            }else{ 
                clearConsole();
                break;
            } 
            
        }while(true); 
       
    }
    
    
    
    
    
    
    public static void enterNewStuMarks(){
        
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                     ADD NEW STUDENT WITH MARKS                                            |");
        System.out.println("--------------------------------------------------------------------------------------------");
        
        
        do{   
            Scanner input=new Scanner(System.in);
            System.out.print("Enter Student ID : ");
            String stuid = input.nextLine();
            if (searchStuID(stuid)!=-1){
                System.out.println(stuid+" is already exists..");
                clearConsole();
                continue;
            }else{
                String []temp1=new String[idArray.length+1];
                for (int i = 0; i < idArray.length; i++) {
                    temp1[i]=idArray[i];
                }
                temp1[temp1.length-1]=stuid;
                idArray=temp1;
            }
            
        
            
            System.out.print("Enter Student Name : ");
            String name= input.nextLine();
                
            String []temp2=new String[namesArray.length+1];
            for (int i = 0; i < namesArray.length; i++) {
                temp2[i]=namesArray[i];
            }
            temp2[temp2.length-1]=name;
            namesArray=temp2;
            
                
            int id=Integer.parseInt(stuid);
            System.out.print("Programming Fundamental System Marks : ");
            int Pmark = input.nextInt();
            if(Pmark>100){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole();
                continue;
            }else if(Pmark<0){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole(); 
                continue;
                }else{
                    int []temp3=new int[idArray.length];
                    for (int i = 0; i < Pmarks.length; i++) {
                        temp3[i]=Pmarks[i];
                    }
                    temp3[id-1]=Pmark;
                    Pmarks=temp3;
                }
              
                
            System.out.print("Database Managemant System Marks : ");
            int Dmark = input.nextInt();
            if(Dmark>100){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole(); 
                continue;
            }else if(Dmark<0){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole(); 
                continue;
                }else{
                    int []temp4=new int[idArray.length];
                    for (int i = 0; i < Dmarks.length; i++) {
                        temp4[i]=Dmarks[i];
                    }
                    temp4[id-1]=Dmark;
                    Dmarks=temp4;
                }  
                          
                Scanner input1=new Scanner(System.in);
                System.out.print("Student has  been added successfully.Do you want to add another (Y/N) : "); 
                String option=input1.nextLine(); 
                if(option.equalsIgnoreCase("y")){
                    clearConsole();
                    continue;
                }else{ 
                    clearConsole();
                    break;
                } 
                            
        }while(true);  
               
           
    }

        
    public static void enterMarks(){
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                               ADD MARKS                                                   |");
        System.out.println("--------------------------------------------------------------------------------------------");
        
        do{
            Scanner input=new Scanner(System.in);
            System.out.print("Enter Student ID : ");
            String stuid = input.nextLine();
            int id=Integer.parseInt(stuid);
            
            if(Pmarks[id-1]!=0){
                System.out.println("This student's marks have been already added.");
                System.out.print("If you want to update the marks,please use[4] update marks option.");
                Scanner input1=new Scanner(System.in);
                System.out.print("Do you want to add another (Y/N) : "); 
                String option=input1.nextLine(); 
                if(option.equalsIgnoreCase("y")){
                    clearConsole();
                    continue;
                }else{ 
                    clearConsole();
                    break;
                } 
            }else{
           
            
            System.out.print("Programming Fundamental System Marks : ");
            int Pmark = input.nextInt();
            if(Pmark>100){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole();
                continue;
            }else if(Pmark<0){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole(); 
                continue;
            }else{
                int []temp3=new int[idArray.length];
                for (int i = 0; i < Pmarks.length; i++) {
                    temp3[i]=Pmarks[i];
                }
                temp3[id-1]=Pmark;
                Pmarks=temp3;
            }
            
        
            System.out.print("Database Managemant System Marks : ");
            int Dmark = input.nextInt();
            if(Dmark>100){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole(); 
                continue;
            }else if(Dmark<0){
                System.out.println("Invalid marks. pleace enter correct marks.");
                clearConsole(); 
                continue;
            }else{
                int []temp4=new int[idArray.length];
                for (int i = 0; i < Dmarks.length; i++) {
                    temp4[i]=Dmarks[i];
                }
                temp4[id-1]=Dmark;
                Dmarks=temp4;
            }  
            
            Scanner input1=new Scanner(System.in);
            System.out.print("Marks added successfully.Do you want to add marks for another student (Y/N) : "); 
            String option=input1.nextLine(); 
            if(option.equalsIgnoreCase("y")){
                clearConsole();
                continue;
            }else{ 
                clearConsole();
                break;
            } 
            }
            
        }while(true);
        
    }
    
    
    public static void updateDetails(){
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                       UPDATE STUDENT DETAILS                                              |");
        System.out.println("--------------------------------------------------------------------------------------------");
        
        
        do{   
            Scanner input=new Scanner(System.in);
            System.out.print("Enter Student ID : ");
            String stuid = input.nextLine();
            int id=Integer.parseInt(stuid);
            if (searchStuID(stuid)!=-1){
                System.out.println("Current name is :"+namesArray[id-1]);
                System.out.print("enter the new student name :");
                String name = input.nextLine();
                namesArray[id-1]=name;
                System.out.println(Arrays.toString(namesArray));
                
                
                Scanner input1=new Scanner(System.in);
                System.out.print("Student details has been updated successfully.Do you want to update another (Y/N) : "); 
                String option=input1.nextLine(); 
                if(option.equalsIgnoreCase("y")){
                    clearConsole();
                    continue;
                }else{ 
                    clearConsole();
                    break;
                } 
                
            }else{
                System.out.println("Invalid student ID.");
            }
            
        }while(true);
    }
    
    
    public static void updateMarks (){
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                               UPDATE MARKS                                               |");
        System.out.println("--------------------------------------------------------------------------------------------");
        
        
        do{   
            Scanner input=new Scanner(System.in);
            System.out.print("Enter Student ID : ");
            String stuid = input.nextLine();
            if (searchStuID(stuid)!=-1){
                int id=Integer.parseInt(stuid);
                System.out.println("Current name is :"+namesArray[id-1]);
                
                if(Pmarks[id-1]==0){
                    System.out.println("This student marks yet to be added");
                }else{
                
                    System.out.println("Current Programming Fundamental System Marks is :"+Pmarks[id-1]);
                    System.out.println("Current Database Managemant System Marks is :"+Dmarks[id-1]);


                    System.out.print("Enter new Programming Fundamental Marks :");
                    int Pmark = input.nextInt();
                    Pmarks[id-1]=Pmark;
                    System.out.print("Enter new Database Managemant System Marks :");
                    int Dmark = input.nextInt();
                    Dmarks[id-1]=Dmark;

                    System.out.println("Marks have been updated successfully");
                    
                    System.out.println(Arrays.toString(idArray)); 
                    System.out.println(Arrays.toString(Pmarks));
                    System.out.println(Arrays.toString(Dmarks)); 

                    
                }
                
                Scanner input1=new Scanner(System.in);
                System.out.print("Do you want to update another (Y/N) : "); 
                String option=input1.nextLine(); 
                if(option.equalsIgnoreCase("y")){
                    clearConsole();
                    continue;
                }else{ 
                    clearConsole();
                    break;
                } 
                
            }else{
                System.out.println("Invalid student ID.");
            }
        }while(true);
        
    }
    
    
    public static void deleteStudent(){
        Scanner input=new Scanner(System.in);
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                               DELETE STUDENT                                              |");
        System.out.println("--------------------------------------------------------------------------------------------");
    
        
        do{
            System.out.print("Input Student Id : ");
            String stId=input.nextLine(); 
            int index=searchStuID(stId);
            if(index==-1){ 
                System.out.println("Invalid student ID.");
                clearConsole(); 

                Scanner input1=new Scanner(System.in);
                    System.out.print("Do you want to search again? (Y/N) : "); 
                    String option=input1.nextLine(); 
                    if(option.equalsIgnoreCase("y")){
                        clearConsole();
                        continue;
                    }else{ 
                        clearConsole();
                        break;
                    } 

            } 
            int length=idArray.length;
            for(int i=index; i<length-1;i++){
                idArray[i]=idArray[i+1];
                namesArray[i]=namesArray[i+1]; 
                Pmarks[i]=Pmarks[i+1]; 
                Dmarks[i]=Dmarks[i+1];
            } 

            String[] tempStIdArray=new String[length-1];
            String[] tempStNameArray=new String[length-1]; 
            int[] tempPrfMarksArray=new int[length-1]; 
            int[] tempDbmsMarksArray=new int[length-1];

            for(int i=0; i<length-1; i++){ 
                tempStIdArray[i]=idArray[i]; 
                tempStNameArray[i]=namesArray[i];
                tempPrfMarksArray[i]=Pmarks[i];
                tempDbmsMarksArray[i]=Dmarks[i];
            } 

            idArray=tempStIdArray;
            namesArray=tempStNameArray;
            Pmarks=tempPrfMarksArray;
            Dmarks=tempDbmsMarksArray;

            System.out.println("Student has been deleted successfully.");

            System.out.println(Arrays.toString(idArray)); 
            System.out.println(Arrays.toString(namesArray));
            System.out.println(Arrays.toString(Pmarks));
            System.out.println(Arrays.toString(Dmarks)); 
            
                    
            
            Scanner input1=new Scanner(System.in);
            System.out.print("Do you want to delete another (Y/N) : "); 
            String option=input1.nextLine(); 
            if(option.equalsIgnoreCase("y")){
                clearConsole();
                continue;
            }else{ 
                clearConsole();
                break;
            } 
        
        
        }while(true);
    }

    
    public static void printStudentDetails(){ 
        Scanner input=new Scanner(System.in);
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                               PRINT STUDENT DETAILS                                      |");
        System.out.println("--------------------------------------------------------------------------------------------");
        
        int total=0;
        double avg=0;
       
       do{
            System.out.print("Enter student id :");
            String stuid=input.nextLine();
            if (searchStuID(stuid)!=-1){
                int id=Integer.parseInt(stuid);
                System.out.println("Current name is :"+namesArray[id-1]);

                System.out.println("-----------------------------------------------------");

                System.out.print("| Programming Fundamentals Marks      |   ");
                System.out.println(Pmarks[id-1]);

                System.out.print("| Database Managemant System Marks    |   "); 
                System.out.println(Dmarks[id-1]);

                System.out.print("| Total Marks                         |   ");
                total=Pmarks[id-1]+Dmarks[id-1];
                System.out.println(total);

                System.out.print("| Avg. Marks                          |   ");
                avg=total/2;
                System.out.println(avg);

                System.out.println("| Rank                                |    ");
                System.out.println("-----------------------------------------------------");

            }else{
                Scanner input1=new Scanner(System.in);
                System.out.print("invalid student ID.Do you want to print another (Y/N) : "); 
                String option=input1.nextLine(); 
                if(option.equalsIgnoreCase("y")){
                    clearConsole();
                    continue;
                }else{ 
                    clearConsole();
                    break;
                } 
            }
                

            
            Scanner input1=new Scanner(System.in);
            System.out.print("Do you want to print another (Y/N) : "); 
            String option=input1.nextLine(); 
            if(option.equalsIgnoreCase("y")){
                clearConsole();
                continue;
            }else{ 
                clearConsole();
                break;
            } 
            
       }while(true);
    } 
     
      
    
    
    public static void BestPFS(){
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                               Best in Programming Fundamentals                            |");
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println();
        System.out.println();
        
        int max=0;
        System.out.println("-----------------------------------------------------------------------"); 
        System.out.print("| ID      ");
        System.out.print("| Name      ");      
        System.out.print("| PF Marks      ");  
        System.out.println("| DBMS Marks      ");        
        System.out.println("-----------------------------------------------------------------------");  
            
         do{ 
            
            int []temp1=new int[idArray.length];
            for (int i = 0; i < Pmarks.length; i++) {
                if(Pmarks[i]>max){
                    max=Pmarks[i];
                }
            temp1[temp1.length-1]=max;
            maxMarks=temp1;
                    
            }
            for (int i = 0; i < maxMarks.length; i++) {
                for (int j = 0; j < Pmarks.length; j++) {
                    if(maxMarks[i]==Pmarks[j]){
                        System.out.print("| "+idArray[j]+"       ");
                        System.out.print("| "+namesArray[j]+"      ");
                        System.out.print("| "+Pmarks[j]+"            ");
                        System.out.println("| "+Dmarks[j]+"      ");
                    }
                }
                
            }
               
            System.out.println("-----------------------------------------------------------------------");  
            
            Scanner input1=new Scanner(System.in);
            System.out.print("Do you want to print another (Y/N) : "); 
            String option=input1.nextLine(); 
            if(option.equalsIgnoreCase("y")){
                clearConsole();
                break;
            }else{ 
                clearConsole();
                break;
            } 
               
        }while(true);
         
    }
    
    
    
    
    
    public static void BestDBMS(){
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                               Best in Database Management System                          |");
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println();
        System.out.println();
        
        int max=0;
        System.out.println("-----------------------------------------------------------------------"); 
        System.out.print("| ID      ");
        System.out.print("| Name      ");  
        System.out.print("| DBMS Marks      "); 
        System.out.println("| PF Marks      ");  
               
        System.out.println("-----------------------------------------------------------------------");  
            
        do{ 
            int []temp1=new int[idArray.length];
            for (int i = 0; i < Dmarks.length; i++) {
                if(Dmarks[i]>max){
                    max=Dmarks[i];
                }
                temp1[temp1.length-1]=max;
                maxMarks=temp1;
            }
            
            for (int i = 0; i < maxMarks.length; i++) {
                for (int j = 0; j < Dmarks.length; j++) {
                    if(maxMarks[i]==Dmarks[j]){
                        System.out.print("| "+idArray[j]+"       ");
                        System.out.print("| "+namesArray[j]+"      ");
                        System.out.print("| "+Dmarks[j]+"      ");
                        System.out.println("|       "+Pmarks[j]+"            ");
                    }
                }
                
            }
               
            System.out.println("-----------------------------------------------------------------------");  
            
            Scanner input1=new Scanner(System.in);
            System.out.print("Do you want to print another (Y/N) : "); 
            String option=input1.nextLine(); 
            if(option.equalsIgnoreCase("y")){
                clearConsole();
                break;
            }else{ 
                clearConsole();
                break;
            } 
               
        }while(true);
         
    }
    
    
    
    
    
    
    public static void main(String[] args) {
       Scanner input=new Scanner(System.in);
       do{
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println("|                     WELCOME TO GDSE MARKS MANAGEMENT SYSTEM                               |");
        System.out.println("--------------------------------------------------------------------------------------------");
        System.out.println();
        System.out.print("[1] Add New Student");
        System.out.println("                     [2] Add New Student With Marks");
        System.out.print("[3] Add Marks");
        System.out.println("                           [4] Update Student Details");
        System.out.print("[5] Update Marks");
        System.out.println("                        [6] Delete Student");
        System.out.print("[7] Print Student Details");
        System.out.println("               [8] Print Student Ranks");
        System.out.print("[9] Best in Programming Fundamentals");
        System.out.println("    [10] Best in Database Managemant System"); 
        System.out.println();


        System.out.print("Enter an option to continue >");
        int option=input.nextInt();
         
        
        
        switch(option){
            case 1:
                enterStudent();
                break;
            case 2:   
                enterNewStuMarks();
                break;
            case 3:
                enterMarks();
                break;
            case 4:   
                updateDetails();
                break;
            case 5:
                updateMarks();
                break;
            case 6:     
                deleteStudent();
                break;
            case 7:
                printStudentDetails();
                break;
            case 8:
            case 9:
                BestPFS();
                break;
            case 10:  
                BestDBMS();
                break;
            default:
                System.out.println("END");
                break;
        }
       } while(true);
        
        }
}
        
        