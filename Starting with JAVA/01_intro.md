## History of JAVA
  - Java was developed by James Gosling at sun microsystem lnc.
  - Java originated at sun microsystem lnc in 1991.
  - Vinod Khosla was the co-founder of sun microsystem.
  - On january 17, 2010, sun microsystem was acquired by Oracle.
  - Java resides in mobiles, client machines, server machines, embedded devices,smart phones, cloud, etc.
  - It shares the same basic features of the language nd libraries.
  - Principle of java : Write Once, Run Everywhere(WORA).
  - what is library: Java library is a collection of predefined classes.
  - You can use thes classes either by inheriting them or instantiating them.
## Java Flavours
  - JAVA SE (core java)
  - JAVA EE (Adavance java)
  - JAVA ME (Micro edition for mobiles)
  - ETC.
# Java complier
![image](https://github.com/user-attachments/assets/cff70d27-9e0c-4d4d-852d-802799b3e118)

- Once you have written the code you save it's called source code then, compile the code using command javac abc.java.
- The compiler checks for syntax errors and any other compile time errors then converts into intermediate code(abc.class file there will n .class file if n class is created in source code) known as bytecode. Bytecode is platform independent, hence it is only understandable by the JVM(which is platform dependent) and not by user or hardware /OS layer.
- This is the start of the Run Time phase, where the bytecode is loaded into the JVM by the class loader(another inbuilt program inside the JVM).
Step 4: Now the bytecode verifier(an inbuilt program inside the JVM) checks the bytecode for its integrity and if not issues are found passes it to the interpreter.
Step 5: Since java is both compiled and interpretted language, now the interpreter inside the JVM converts each line of the bytecode into executable machine code and passed it to the OS/Hardware i.e. the CPU to execute.
These are the standard steps involved in a typical java program execution scenario.

Working of JIT (Just-In-Time) Compiler
In the above steps we didn’t mention the working of JIT compiler. Lets understand this by taking 2 case examples –

java jit compiler working

In case 2 we have the JIT compiler. Now before the bytecode is passed onto the interpreter for conversion to machine code, the JIT compiler scans the full code to see if it can be optimized. As it finds the last line is redundant it removes it from the bytecode and passes only 4 lines to the interpreter thus making it more efficient and faster as the interpreter now has 1 line less to interpret.
So this is how JIT compiler speeds up the overall execution process.
This was just one scenario where JIT compiler can help in making the execution process fast and efficient. There are other cases like inclusion of only those packages needed in the code, code optimizations, redundant code removal etc which overall makes the process very fast and efficient. Also different JITs developed by different companies work differently and JIT compilers are an optional step and not invoked everytime.
 
