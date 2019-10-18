# simple-calculator


package eg.edu.alexu.csd.oop.calculator.cs13;
import javax.swing.*;
import java.lang.*;
public class Main {
    public static void main(String[] args) {
        SuperCalculator calc=new SuperCalculator();
        calc.pack();
        calc.setLocationRelativeTo(null);
        calc.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        calc.setVisible(true);
    }
}


package eg.edu.alexu.csd.oop.calculator.cs13;
public interface Calculator {
    public void input(String s);
    public String getResult();
    public String current ();
    public String prev();
    public String next();
    public void save();
    public void load();
}



package eg.edu.alexu.csd.oop.calculator.cs13;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.util.*;
import java.io.*;
import java.lang.*;
public class SuperCalculator extends JFrame implements Calculator{
    private JButton num0;
    private JButton num1;
    private JButton num2;
    private JButton num3;
    private JButton num4;
    private JButton num5;
    private JButton num6;
    private JButton num7;
    private JButton num8;
    private JButton num9;
    private JButton add;
    private JButton subtract;
    private JButton multiply;
    private JButton divide;
    private JButton equal;
    private JButton clear;
    private JButton point;
    private JButton prev;
    private JButton next;
    private JButton save;
    private JButton load;
    private double temp1;
    private double temp2;
    public double finalTemp;
    public JTextField write;
    public JLabel result;
    private boolean addBool;
    private boolean subBool;
    private boolean multiplyBool;
    private boolean divideBool;
    private String sentence="";
    private String sentence2="";
    public String[] file=new String[20];
    public int k=0;
    public SuperCalculator(){
        super("Calculator");
        JPanel p1=new JPanel();
        p1.setLayout(new GridLayout(4,3));
        p1.add(num1=new JButton("1"));
        p1.add(num2=new JButton("2"));
        p1.add(num3=new JButton("3"));
        p1.add(num4=new JButton("4"));
        p1.add(num5=new JButton("5"));
        p1.add(num6=new JButton("6"));
        p1.add(num7=new JButton("7"));
        p1.add(num8=new JButton("8"));
        p1.add(num9=new JButton("9"));
        p1.add(num0=new JButton("0"));
        p1.add(point=new JButton("."));
        p1.add(clear=new JButton("c"));
        JPanel p2=new JPanel();
        p2.setLayout(new GridLayout(5,1));
        p2.add(add=new JButton("+"));
        p2.add(subtract=new JButton("-"));
        p2.add(multiply=new JButton("*"));
        p2.add(divide=new JButton("/"));
        p2.add(equal=new JButton("="));
        add.setEnabled(false);
        subtract.setEnabled(false);
        multiply.setEnabled(false);
        divide.setEnabled(false);
        equal.setEnabled(false);
        JPanel p3=new JPanel();
        p3.setLayout(new GridLayout(6,1));
        p3.add(write=new JTextField(20));
        p3.add(result=new JLabel());
        p3.add(prev=new JButton("prev"));
        p3.add(next=new JButton("next"));
        p3.add(save=new JButton("save"));
        p3.add(load=new JButton("load"));
        write.setHorizontalAlignment(JTextField.RIGHT);
        result.setHorizontalAlignment(JTextField.LEFT);
        write.setEditable(false);
        prev.setEnabled(false);
        next.setEnabled(false);
        save.setEnabled(false);
        JPanel p=new JPanel();
        p.setLayout(new GridLayout());
        p.add(p1,BorderLayout.SOUTH);
        p.add(p2,BorderLayout.EAST);
        p.add(p3,BorderLayout.NORTH);
        add(p);
        num0.addActionListener(new FunctionOfZero());
        num1.addActionListener(new FunctionOfOne());
        num2.addActionListener(new FunctionOfTwo());
        num3.addActionListener(new FunctionOfThree());
        num4.addActionListener(new FunctionOfFour());
        num5.addActionListener(new FunctionOfFive());
        num6.addActionListener(new FunctionOfSix());
        num7.addActionListener(new FunctionOfSeven());
        num8.addActionListener(new FunctionOfEight());
        num9.addActionListener(new FunctionOfNine());
        point.addActionListener(new FunctionOfPoint());
        clear.addActionListener(new FunctionOfClear());
        add.addActionListener(new FunctionOfAdd());
        subtract.addActionListener(new FunctionOfSubtract());
        multiply.addActionListener(new FunctionOfMultiply());
        divide.addActionListener(new FunctionOfDivide());
        equal.addActionListener(new FunctionOfEqual());
        prev.addActionListener(new FunctionOfUndo());
        next.addActionListener(new FunctionOfRedo());
        save.addActionListener(new FunctionOfSave());
        load.addActionListener(new FunctionOfLoad());
    }
    public class FunctionOfZero implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"0");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfOne implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"1");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfTwo implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"2");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfThree implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"3");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfFour implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"4");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfFive implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"5");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfSix implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"6");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfSeven implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"7");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfEight implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"8");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfNine implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+"9");
            if(!sentence.contains("+")&&!sentence.contains("-")&&!sentence.contains("*")&&!sentence.contains("/")) {
                add.setEnabled(true);
                subtract.setEnabled(true);
                multiply.setEnabled(true);
                divide.setEnabled(true);
                equal.setEnabled(false);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }else {
                add.setEnabled(false);
                subtract.setEnabled(false);
                multiply.setEnabled(false);
                divide.setEnabled(false);
                equal.setEnabled(true);
                prev.setEnabled(false);
                next.setEnabled(false);
                save.setEnabled(false);
                load.setEnabled(false);
            }
        }
    }
    public class FunctionOfPoint implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence=write.getText();
            write.setText(sentence+".");
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(false);
            next.setEnabled(false);
            save.setEnabled(false);
            load.setEnabled(false);
        }
    }
    public class FunctionOfClear implements ActionListener{
        public void actionPerformed(ActionEvent event){
            write.setText("");
            addBool=false;
            subBool=false;
            multiplyBool=false;
            divideBool=false;
            temp1=0;
            temp2=0;
            finalTemp=0;
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(true);
            next.setEnabled(true);
            save.setEnabled(true);
            load.setEnabled(true);
        }
    }
    public class FunctionOfAdd implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence="";
            temp1=0;
            sentence+=write.getText();
            temp1=Double.parseDouble(sentence);
            write.setText(sentence+"+");
            addBool=true;
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(false);
            next.setEnabled(false);
            save.setEnabled(false);
            load.setEnabled(false);
        }
    }
    public class FunctionOfSubtract implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence="";
            temp1=0;
            sentence+=write.getText();
            if(!sentence.contains("*")&&!sentence.contains("/")) {
                temp1 = Double.parseDouble(sentence);
                write.setText(sentence+"-");
                subBool=true;
            }else{
                sentence=sentence.substring(0,sentence.length()-1);
                temp1 = Double.parseDouble(sentence);
                write.setText(write.getText()+"-");
                subBool=false;
            }
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(false);
            next.setEnabled(false);
            save.setEnabled(false);
            load.setEnabled(false);
        }
    }
    public class FunctionOfMultiply implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence="";
            temp1=0;
            sentence+=write.getText();
            temp1=Double.parseDouble(sentence);
            write.setText(sentence+"*");
            multiplyBool=true;
            add.setEnabled(false);
            subtract.setEnabled(true);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(false);
            next.setEnabled(false);
            save.setEnabled(false);
            load.setEnabled(false);
        }
    }
    public class FunctionOfDivide implements ActionListener{
        public void actionPerformed(ActionEvent event){
            sentence="";
            temp1=0;
            sentence+=write.getText();
            temp1=Double.parseDouble(sentence);
            write.setText(sentence+"/");
            divideBool=true;
            add.setEnabled(false);
            subtract.setEnabled(true);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(false);
            next.setEnabled(false);
            save.setEnabled(false);
            load.setEnabled(false);
        }
    }
    private String sentence1="";
    public void input(String s){
        sentence=s;
        for(int w=0;w<sentence.length();w++){
            if(sentence.charAt(w)=='+'||sentence.charAt(w)=='-'||sentence.charAt(w)=='*'||sentence.charAt(w)=='/'){
                for(int f=0;f<w;f++){
                    sentence1+=sentence.charAt(f);
                }
                break;
            }
        }
        sentence2="";
        temp1=Double.parseDouble(sentence1);
        for(int i=0;i<sentence.length();i++){
            if(sentence.charAt(i)=='+'||sentence.charAt(i)=='-'||sentence.charAt(i)=='*'||sentence.charAt(i)=='/'){
                for(int j=i+1;j<sentence.length();j++){
                    sentence2+=sentence.charAt(j);
                }
                break;
            }
        }
        temp2=Double.parseDouble(sentence2);
        for(int i=0;i<sentence.length();i++){
            if(sentence.charAt(i)=='+'||sentence.charAt(i)=='-'||sentence.charAt(i)=='*'||sentence.charAt(i)=='/'){
                if(sentence.charAt(i)=='+'){
                    finalTemp=temp1+temp2;
                }
                else if(sentence.charAt(i)=='-'){
                    finalTemp=temp1+temp2;
                }
                else if(sentence.charAt(i)=='*'){
                    finalTemp=temp1*temp2;
                }
                else if(sentence.charAt(i)=='/'){
                    finalTemp=temp1/temp2;
                }
            }
        }
        write.setText(s);
        result.setText("");
    }
    public int g;
    public class FunctionOfEqual implements ActionListener{
        public void actionPerformed(ActionEvent event){
            finalTemp=0;
            sentence=write.getText();
            sentence2="";
            for(int i=0;i<sentence.length();i++){
                if(sentence.charAt(i)=='+'||sentence.charAt(i)=='-'||sentence.charAt(i)=='*'||sentence.charAt(i)=='/'){
                    for(int j=i+1;j<sentence.length();j++){
                        sentence2+=sentence.charAt(j);
                    }
                    break;
                }
            }
            temp2=Double.parseDouble(sentence2);
            sentence2="";
            if(addBool==true){
                finalTemp=temp1+temp2;
                result.setText(""+sentence+"="+Double.toString(finalTemp));
                write.setText("");
            }
            else if(subBool==true){
                finalTemp=temp1-temp2;
                result.setText(""+sentence+"="+Double.toString(finalTemp));
                write.setText("");
            }
            else if(multiplyBool==true){
                finalTemp=temp1*temp2;
                result.setText(""+sentence+"="+Double.toString(finalTemp));
                write.setText("");
            }
            else if(divideBool==true){
                if(temp2==0){
                    result.setText(""+sentence+"="+"ERROR!");
                    write.setText("");
                }else {
                    finalTemp = temp1 / temp2;
                    result.setText(""+sentence+"="+Double.toString(finalTemp));
                    write.setText("");
                }
            }
            addBool=false;
            subBool=false;
            multiplyBool=false;
            divideBool=false;
            file[k]=result.getText();
            g=k;
            k++;
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(true);
            next.setEnabled(true);
            save.setEnabled(true);
            load.setEnabled(true);
        }
    }
    public String getResult(){
        write.setText(sentence+"="+finalTemp);
        return Double.toString(finalTemp);
    }
    public String current(){
        write.setText("");
        result.setText(sentence+"="+finalTemp);
        file[k]=result.getText();
        g=k;
        k++;
        return result.getText();
    }
    public class FunctionOfUndo implements ActionListener{
        public void actionPerformed(ActionEvent event){
            if(g>0) {
                g--;
                result.setText(file[g]);
            }else {
                g--;
                result.setText("ERROR!");
            }
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(true);
            next.setEnabled(true);
            save.setEnabled(true);
            load.setEnabled(true);
        }
    }
    public String prev() {
        add.setEnabled(false);
        subtract.setEnabled(false);
        multiply.setEnabled(false);
        divide.setEnabled(false);
        equal.setEnabled(false);
        prev.setEnabled(true);
        next.setEnabled(true);
        save.setEnabled(true);
        load.setEnabled(true);
        if (g > 0) {
            g--;
            result.setText(file[g]);
            return (file[g]);
        } else {
            g--;
            result.setText("ERROR!");
            return ("ERROR!");
        }
    }
    public class FunctionOfRedo implements ActionListener{
        public void actionPerformed(ActionEvent event){
            if(g<k-1){
                g++;
                result.setText(file[g]);
            }else {
                g++;
                result.setText("ERROR!");
            }
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(true);
            next.setEnabled(true);
            save.setEnabled(true);
            load.setEnabled(true);
        }
    }
    public String next(){
        add.setEnabled(false);
        subtract.setEnabled(false);
        multiply.setEnabled(false);
        divide.setEnabled(false);
        equal.setEnabled(false);
        prev.setEnabled(true);
        next.setEnabled(true);
        save.setEnabled(true);
        load.setEnabled(true);
        if(g<k-1){
            g++;
            result.setText(file[g]);
            return (file[g]);
        }else {
            g++;
            result.setText("ERROR!");
            return ("ERROR!");
        }
    }
    Formatter y;
    Scanner x;
    public class FunctionOfSave implements ActionListener{
        public void actionPerformed(ActionEvent event){
            try {
                y=new Formatter("save.txt");
            }
            catch (Exception e){
                System.out.println("ERROR!");
            }
            y.format("%s\n%s\n%s\n%s\n%s",(g>=0)? file[g] : " ",(g>=1)? file[g-1]: " ",(g>=2)? file[g-2]:" ",(g>=3)? file[g-3]:" ",(g>=4)? file[g-4]:" ");
            y.close();
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(true);
            next.setEnabled(true);
            save.setEnabled(true);
            load.setEnabled(true);
        }
    }
    public void save(){
        try {
            y=new Formatter("save.txt");
        }
        catch (Exception e){
            System.out.println("ERROR!");
        }
        y.format("%s\n%s\n%s\n%s\n%s",(g>=0)? file[g] : " ",(g>=1)? file[g-1]: " ",(g>=2)? file[g-2]:" ",(g>=3)? file[g-3]:" ",(g>=4)? file[g-4]:" ");
        y.close();
        add.setEnabled(false);
        subtract.setEnabled(false);
        multiply.setEnabled(false);
        divide.setEnabled(false);
        equal.setEnabled(false);
        prev.setEnabled(true);
        next.setEnabled(true);
        save.setEnabled(true);
        load.setEnabled(true);
    }
    public class FunctionOfLoad implements ActionListener{
        public void actionPerformed(ActionEvent event){
            try {
                x=new Scanner(new File("save.txt"));
            }
            catch (Exception e){
                System.out.println("ERROR!");
            }
            while (x.hasNext()) {
                String a = x.nextLine();
                String b = x.nextLine();
                String c = x.nextLine();
                String d = x.nextLine();
                String e = x.nextLine();
                result.setText(a+","+b+","+c+","+d+","+e);
            }
            add.setEnabled(false);
            subtract.setEnabled(false);
            multiply.setEnabled(false);
            divide.setEnabled(false);
            equal.setEnabled(false);
            prev.setEnabled(true);
            next.setEnabled(true);
            save.setEnabled(true);
            load.setEnabled(true);
        }
    }
    public void load(){
        try {
            x=new Scanner(new File("save.txt"));
        }
        catch (Exception e){
            System.out.println("ERROR!");
        }
        while (x.hasNext()) {
            String a = x.nextLine();
            String b = x.nextLine();
            String c = x.nextLine();
            String d = x.nextLine();
            String e = x.nextLine();
            result.setText(a+","+b+","+c+","+d+","+e);
        }
        add.setEnabled(false);
        subtract.setEnabled(false);
        multiply.setEnabled(false);
        divide.setEnabled(false);
        equal.setEnabled(false);
        prev.setEnabled(true);
        next.setEnabled(true);
        save.setEnabled(true);
        load.setEnabled(true);
    }
}
