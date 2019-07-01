# use it with command line 
- add environment varibale to point to `JUNIT_HOME`  as where jar file is located.
- set path using `set classpath=%JUNIT_HOME%\junit-2.14.jar`
- move code file to `JUNIT_HOME`
- compile file using `javac -cp .;junit-2.14.jar calc.java` 
- run with `java -cp .;junit-2.14.jar;hancert.jar org.junit.runner.JUnitCore calcTest` 



