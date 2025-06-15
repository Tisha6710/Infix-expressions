# Infix-expressions
package Stacks;
import java.util.*;
public class Infix {
    public static void main(String[] args) {
        String str="7-1+7*5/3";
        Stack<Integer>val=new Stack<>();
        Stack<Character> op=new Stack<>();
        for(int i=0;i<str.length();i++){
            char ch= str.charAt(i);
            int ascii =(int) ch;
            // numbers as charcters
            // like 0 ki ascii value hoti h 48 and 9 ki hoti h 57 means 48 to 57
            if(ascii>=48 && ascii<=57) val.push(ascii-48); // if char is 5 means ascii val is
                                          // 53 toh yhn par yahan par 53-48 hua hai that is 5
                                          // kiyuki hume 5 chahiye
            else if(op.size()==0) op.push(ch);
            else{   // priority wala
               if(ch=='+' || ch=='-') {
                   // work
                   int v2 = val.pop();
                   int v1 = val.pop();
                   if (op.peek() == '-') val.push(v1 - v2);
                   if (op.peek() == '+') val.push(v1 + v2);
                   if (op.peek() == '*') val.push(v1 * v2);
                   if (op.peek() == '/') val.push(v1 / v2);
                   op.pop();
                   op.push(ch);
               }
                   if(ch=='*' || ch=='/'){
                       if(op.peek()=='*' || op.peek()=='/'){
                           // work
                           int v2 = val.pop();
                           int v1 = val.pop();
                           if (op.peek() == '-') val.push(v1 - v2);
                           if (op.peek() == '+') val.push(v1 + v2);
                           if (op.peek() == '*') val.push(v1 * v2);
                           if (op.peek() == '/') val.push(v1 / v2);
                           op.pop();

                           op.push(ch);

                       }
                       else op.push(ch);


               }
            }



        }
        // val wale ko stack ko 1 banana h
        while(val.size()>1){
            int v2=val.pop();
            int v1=val.pop();
            if (op.peek() == '-') val.push(v1 - v2);
            if (op.peek() == '+') val.push(v1 + v2);
            if (op.peek() == '*') val.push(v1 * v2);
            if (op.peek() == '/') val.push(v1 / v2);
            op.pop();
        }
        System.out.println(val.peek());
    }

}
