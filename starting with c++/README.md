## History of C++
  - Bjarne Stroustrup created c++.
  - According to hime c++ is extended version of c, where he introduced concept of classes in 1979. in AT & T's Bell Labs.
  - Early name of c++ was **c with classes** it's officially became c++ in 1983.

## Facts about c++
  + c++'s OOP aspect was inspired by a computer simulation language called simula67.
  + **java** is written in c++.
  + Major operating systems of modern times are written in c++, along with some famous libraries like numpy.
## Features of C++
  - C++ is a **middle level language**
      - it's mean it can behave like low level as well as high level language.
      - low level language which uses to create system dependent programs like operating system, drivers, etc.
      - High level language use to create software that are independent of OS.
  - C++ supports principles of **object-oriented** paradigm.
  - c++ joins three separate programming traditions.
      - The **procedural language** tradition, represented by c.
      - The **object-oriented** language tradition, represented by the class enhancements c++ adds to c.
      - **Generic programming**, supported by c++ templates.
## comparison between c and c++
  - c++ is a super set of c language.
  - c++ programs can use existing c software libraries.
  - c follows **top-down** approach of programming.
      - **Top-down** means first we define the outline of program then after we define its code snipper like function, etc.
  - c++ follws bottom-up approach of programming
      - its mean that we need to define the definition of all function thenwe struture the program.
  - c adopts **procedure oriented** programming.
  - c++ adopts **object-oriented** programming.
      - OOPs is a programming approach which revolves around the concept of **object**.
      - that can be defined as a set of properties and set of operations performed using entity's property set, is known as object.
## Concept of Classes and Object
  - class is blueprint of an object.
  - class is description of object's property set and set of operations.
  - creating class is as good as defining a new data type
  - class is a means to achieve encapsulation
  - object is a run time entity
  - object is an instance of class.

# Software development in c/c++
![image](https://github.com/user-attachments/assets/31009a26-1dcc-41e3-a24f-17a008ecb208)

## Identifier in c++
  - constant
      - any information is constant.
      - data = information = constant
    - type of constant
        - primary
            - integer (23, -34, 0, etc)
            - real (3.4, -0.06, etc)
            - character ('a', '4', '-', '&', etc)
        - secondary
            - created from primary identifiers
            - array, string, pointer, union, structure, enumerator, class
  - variables
      - variables are the name of memory locations where we store data.
      - variables name is any combination of alphabet (a to z or A to Z), digit(0 to 9) and underscore(_).
      - valid variable cannot start with digit.
  - keywords
      |||||||
      |------|--------|------|--------|----|---------|
      | auto | double | int | struct | asm | private |
      | break| else | long | switch | catch | public |
      | case | enum | register | typedef | class | protected|
      | char| extern | return | union | delete | template|
      |const| float| short| unsigned| friend| this|
      | continue| for| signed| void| inline| throw|
      |default| goto| sizeof| volatile| new|try|
      | do| if| static| while| operator|try|

## Data type
  | int | char | float | double | void |
  |-----|------|-------|--------|------|
  |2 bytes|1 bytes|4 bytes|8 bytes||
  |int a=4;|char c='a';|float f=4.6;|double d;|
  - assignment operator(=), like 5 assigned to b
  - unlikeee c, you can declare variables even after-action statements.
    
## output instruction
  - in c, standard output device is monitor and printf() is use to send data/message to monitor.
  - printf() is predefined function
  - in c++, we can use cout to send data/message to monitor.
  - cout is predefined object
  - the operator << is called insertion or put to operator.
  - printf("hello");       count << "hello"'
  - printf("sum of %d and %d is %d", a, b, c);     count<<"sum of "<<a<<" and "<<b<<"is "<<c;
  - first we insert "sum of " in double quote then, we insert variable a then "is" then b and eventually c.
  - printf("%d", a+b);     count<<a+b;

## input insttuction
  - in c, standard input device is keyboard and scanf() is use to receive data from keyboard.
  - scanf() is a predefined function
  - in c++, we can use cin to input data from keyboard
  - the identifier cin is a predefiend object in c++
  - the oprator >> is known as extraction or get from operator.
  - scanf("%d", &a);     cin>>a;
  - scanf("%d%f, &a, &b);    cin>>a>>b;
## Remember
  -	According to the ANSI standards for C language, explicit declaration of function is recommended but not mandatory.
  - ANSI standards for C++ language says explicit declaration of function is compulsory.

## Header Files
  -	Predefined functions are declared in header files, so whenever you are using any predefined function in your code, you have to include specific header file that contains its declaration.

## About iostream.h
-	We need to include header file iostream.h, it contains declarations for the identifier cout and the operator <<. And also, for the identifier cin and operator >>.
-	Header files contain declaration of identifiers.

## endl
-	Inserting endl into the output stream causes the screen cursor to move to the beginning of the next line.
-	endl is a manipulator and it is declared in iostream.h
-	‘\n’ character also works as it works in C.
