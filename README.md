# Strings
All the concepts of Strings Data Structure.


import java.util.*;

public class Strings {
    static final int CHAR=256;

    public static void printfreq(String str){

        int count[]=new int[26];   //new array to store the elements
        int n=str.length();

        for(int i=0;i<n;i++){
            count[str.charAt(i)-'a']++;
              
        }
        for(int i=0;i<26;i++)
        {
            if(count[i]>0)
            System.out.println((char)(i+'a')+ " " +count[i]);
        }

    }

         public static boolean palindrome(String str){

            int begin=0;
            int end=str.length()-1;

            while(begin<end){

                if(str.charAt(begin)!=str.charAt(end))
                   { return false;

                   }
                    begin++;
                    end--;    
            }
            return true;
         }

         //problem 1:subsequence 

         public static boolean subsequence(String s1,String s2){

            int n=s1.length()-1;
            int m=s2.length()-1;

            int j=0;
            if(n<m)return false;
            
            for(int i=0;i<n && j<m;i++)
            {
                    if(s1.charAt(i)==s2.charAt(j))
                    j++;
            }
            return(j==m);
         }

         //problem 2 :anagram ("Silent " , "listen")

         public static boolean anagram(String s1,String s2){

            int n=s1.length()-1;
            int m=s2.length()-1;

            //take lengths positive
            System.out.println( n +" "+ m);
            if(n!=m)return false;

            int count[]=new int[CHAR];

            for(int i=0;i<n;i++){

                count[s1.charAt(i)]++;
                count[s2.charAt(i)]--;
            }

            for(int i=0;i<CHAR;i++){
                if(count[i]!=0)return false;
            }
            return true;
         }

         //problem 3: Leftmost repeating character

         public static int leftmostrepeating(String str){

            int count[]=new int[CHAR];

            for(int i=0;i<str.length();i++){

                count[str.charAt(i)]++;
            }
            for(int i=0;i<CHAR;i++){

                if(count[str.charAt(i)]>1)
                return i;
            }
            return -1;
         }


         //problem 4:Leftmost Non-Repeatingcharacter
         public static int leftmostNonrepeatingcharacter(String str){

            int count[]=new int[CHAR];

            for(int i=0;i<str.length();i++){
                count[str.charAt(i)]++;
            }

            for(int i=0;i<CHAR;i++){

                if(count[str.charAt(i)]==1)return i;
            }
            return -1;
         }

         //problem :5 Reverse the sentence

         public static void reversewords(char[] s,int n){
            int start=0;
            for(int end=0;end<n;end++){

                if(s[end]==' '){

                    reverse(s,start,end-1);
                    start=end+1;
                }
            }
            reverse(s,start,n-1);
            reverse(s,0,n-1);
            }

            public static void reverse(char s[],int low,int high){

                while(low<=high){

                    char temp=s[low];
                    s[low]=s[high];
                    s[high]=temp;
                    low++;
                    high--;
                }

            }

            //problem:6  (Pattern Searching) Naive approach

            public static void Pattern(String txt,String pat){

                int n=txt.length();
                int m=pat.length();

                for(int i=0;i<=(n-m);i++){
                   int j;
                    for(j=0;j<m;j++)
                        if(pat.charAt(j)!=txt.charAt(i+j))
                            break;
                          if(j==m)
                        System.out.println(i + " ");
                }   
            }

             //problem:6  (Pattern Searching) Better  approach
             
            public static void Pattern2(String txt,String pat){

                int n=txt.length();
                int m=pat.length();

                for(int i=0;i<=(n-m);i++){
                   int j;
                    for(j=0;j<m;j++)
                        if(pat.charAt(j)!=txt.charAt(i+j))
                            break;
                          if(j==m)
                        System.out.println(i + " ");

                        if(j==0){
                            i++;
                        }
                        else{
                           i= (i+j);
                        }
                }   
            }

            //Rabin karp algorithm
            //kmp




            //problem :String are rotation
            
            public static boolean rotationcheck(String s1,String s2) 
            {

                if(s1.length()!=s2.length()) 
                { 
                    return false;
                }
                 String temp=s1+s1;
                 return temp.indexOf(s2)!=-1;
                             
            }

    public static void main(String args[]){

       // String str="geeksforgeeks";
       // printfreq(str);
     //  String str="ABCDCBA";
      // System.out.println(palindrome(str));

     // String s1="geeksforgeeks";
     // String s2="grges";

     // System.out.println(subsequence(s1, s2));

    // String s1="listen";
    // String s2="silent";

     //System.out.println(anagram(s1, s2));
     //String str="abbcc";
     //System.out.println(leftmostrepeating(str));

    // String str="geeksforgeeks";
    // System.out.println(leftmostNonrepeatingcharacter(str));

    //  String str="welcome to gfg";
    //  int n=str.length();
    //  char[] s=str.toCharArray();            //changing it in character array
       
    //  System.out.println("After reversing the sentence");
        //      reversewords(s, n);
          //    System.out.println(s);

         // String txt="ABABABCD";
         // String pat="ABCD";
             //   Pattern(txt, pat);

             String s1="ABCD";
             String s2="CDAB";
               
             System.out.println(rotationcheck(s1, s2));
             
    }
    
}

