# Comp-11.Lab


import java.util.Scanner; 
import java.io.*; 
public class Comp11Lab {

    public static void main(String[] args) {
		 int creditHrs; // number of semester hours earned 
		 double qualityPts; // number of quality points earned 
		 double gpa; // grade point (quality point) average 

		 String line, name; 
                 String inputName = "students.dat"; 
		 String outputName = "warning.dat"; 	
		 
		 try
		 { 
			 
                          // Set up scanner to input file 
                          Scanner scan = new Scanner(new File
                            ("D:\\Test/students.dat"));
			 
			 // Set up the output file stream 
			 PrintWriter outFile= new PrintWriter(new FileWriter
                            ("D:\\Test/output.txt"));
			 
                        // Print a header to the output file 
			 outFile.println (); 
			 outFile.println ("Students on Academic Warning"); 
			 outFile.println (); 
			
			 // Process the input file, one token at a time 	
			 while (scan.hasNext())     
			 { 
				 name=scan.next();      
				 creditHrs=scan.nextInt();
				 qualityPts=scan.nextDouble();
				 gpa=qualityPts/creditHrs;     
				 line=name +" "+ gpa;
                                 
				 //outFile.print(line);
				 if ((creditHrs < 30 && gpa < 1.5) ||
                                     (creditHrs < 60 && gpa < 1.75) ||
                                     (creditHrs >= 60 && gpa < 2.0)){
                                     outFile.println(name + " " + creditHrs + " " + gpa);
                                 }
                    
			 } 
			 //outFile.println ("test"); 
			 outFile.close();
		 } 
		 catch (FileNotFoundException e)     
		 { 
			 System.out.println ("The file " + inputName + " was not found.");     
		 } 
		 catch (IOException e)     
		 { 
			 System.out.println("Format error in input file: " + e);     
		 } 
		 catch (NumberFormatException e)     
		 { 
			 System.out.println ("Format error in input file: " + e);     
		 } 
	 } 
}
