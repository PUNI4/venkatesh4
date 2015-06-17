# venkatesh4
Code for File creation
//Code Sample

import java.io.File;
import java.io.IOException;
import java.util.Scanner;
import java.io.*;

//Simple Java program to create File and Directory in Java


public class FileDemo {

    public static void main(String args[]) throws IOException {

        Scanner reader = new Scanner(System.in);
        boolean success = false;

        System.out.println("Enter path of directory to create");
        String dir = reader.nextLine();

        // Creating new directory in Java, if it doesn't exists
        File directory = new File(dir);
        if (directory.exists()) {
            System.out.println("Directory already exists ...");

        } else {
            System.out.println("Directory not exists, creating now");

            success = directory.mkdir();
            if (success) {
                System.out.printf("Successfully created new directory : %s%n", dir);
            } else {
                System.out.printf("Failed to create new directory: %s%n", dir);
            }
        }

        // Creating new file in Java, only if not exists
        System.out.println("Enter file name to be created ");
        String filename = reader.nextLine();

        File f = new File(filename);
        if (f.exists()) {
            System.out.println("File already exists");

        } else {
            System.out.println("No such file exists, creating now");
            success = f.createNewFile();
            if (success) {
                System.out.printf("Successfully created new file: %s%n", f);
		 PrintWriter out = null;
  		BufferedWriter bw = null;
 		 FileWriter fw = null;
  		try{
     			fw = new FileWriter("outfilename", true);
     			bw = new BufferedWriter(fw);
    			out = new PrintWriter(bw);
     			out.println("the text");
  		    }
  		catch( IOException e ){
     			// File writing/opening failed at some stage.
  			}
 		 finally{
   		  try{
   		     if( out != null ){
    				       out.close(); // Will close bw and fw too
     			   }
     		   else if( bw != null ){
      		     bw.close(); // Will close fw too
      			  }
       			 else if( fw != null ){
       			    fw.close();
      			  }
      			  else{
          		 // Oh boy did it fail hard! :3
        		}
     		}
     	catch( IOException e ){
       	 // Closing the file writers failed for some obscure reason
     	}
  	} 
           	 } else {
           	     System.out.printf("Failed to create new file: %s%n", f);
           	 }
        	}

        // close Scanner to prevent resource leak
        reader.close();




copying file1 to file2
=======================

class FileDemo {
    public static void main(String args[]) {
      try {
          FileReader fr=new FileReader("1.txt");
          FileWriter fw=new FileWriter("2.txt");
          int c=fr.read();
          while(c!=-1) {
            fw.write(c);
          }
      } catch(IOException e) {
          System.out.println(e);
      } finally() { 
          fr.close();
          fw.close();
      }
    }
}
