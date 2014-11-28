## Compile and Execute java file by manual
- Compile

        [16:59:13.56 C:\hello-world\src\main\java]
        $ javac com\juvenxu\mvnbook\helloworld\HelloWorld.java

- Execute

        [16:59:20.89 C:\hello-world\src\main\java]
        $ java com.juvenxu.mvnbook.helloworld.HelloWorld
        Hello Maven

## Compile and Execute by maven
- Compile

        [16:55:49.04 C:\hello-world]
        $ mvn clean compile
        [INFO] Scanning for projects...
        [INFO]
        [INFO] ------------------------------------------------------------------------
        [INFO] Building Maven Hello World Project 1.0-SNAPSHOT
        [INFO] ------------------------------------------------------------------------
        [INFO]
        [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ hello-world ---
        [INFO] Deleting C:\Marslo\Study\Codes\Maven\hello-world\target
        [INFO]
        [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ hello-world ---
        [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
        [INFO] skip non existing resourceDirectory C:\Marslo\Study\Codes\Maven\hello-world\src\main\resources
        [INFO]
        [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ hello-world ---
        [INFO] Changes detected - recompiling the module!
        [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
        [INFO] Compiling 1 source file to C:\Marslo\Study\Codes\Maven\hello-world\target\classes
        [INFO] ------------------------------------------------------------------------
        [INFO] BUILD SUCCESS
        [INFO] ------------------------------------------------------------------------
        [INFO] Total time: 1.916 s
        [INFO] Finished at: 2014-11-28T17:02:36+08:00
        [INFO] Final Memory: 12M/150M
        [INFO] ------------------------------------------------------------------------

- Test

        [17:02:39.17 C:\hello-world]
        $ mvn clean test
        [INFO] Scanning for projects...
        [INFO]
        [INFO] ------------------------------------------------------------------------
        [INFO] Building Maven Hello World Project 1.0-SNAPSHOT
        [INFO] ------------------------------------------------------------------------
        [INFO]
        [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ hello-world ---
        [INFO] Deleting C:\Marslo\Study\Codes\Maven\hello-world\target
        [INFO]
        [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ hello-world ---
        [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
        [INFO] skip non existing resourceDirectory C:\Marslo\Study\Codes\Maven\hello-world\src\main\resources
        [INFO]
        [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ hello-world ---
        [INFO] Changes detected - recompiling the module!
        [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
        [INFO] Compiling 1 source file to C:\Marslo\Study\Codes\Maven\hello-world\target\classes
        [INFO]
        [INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ hello-world ---
        [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
        [INFO] skip non existing resourceDirectory C:\Marslo\Study\Codes\Maven\hello-world\src\test\resources
        [INFO]
        [INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ hello-world ---
        [INFO] Changes detected - recompiling the module!
        [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
        [INFO] Compiling 1 source file to C:\Marslo\Study\Codes\Maven\hello-world\target\test-classes
        [INFO]
        [INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ hello-world ---
        [INFO] Surefire report directory: C:\Marslo\Study\Codes\Maven\hello-world\target\surefire-reports

        -------------------------------------------------------
         T E S T S
        -------------------------------------------------------
        Running com.juvenxu.mvnbook.helloworld.HelloWorldTest
        Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.06 sec

        Results :

        Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

        [INFO] ------------------------------------------------------------------------
        [INFO] BUILD SUCCESS
        [INFO] ------------------------------------------------------------------------
        [INFO] Total time: 4.639 s
        [INFO] Finished at: 2014-11-28T17:03:42+08:00
        [INFO] Final Memory: 13M/159M
        [INFO] ------------------------------------------------------------------------

- Package

        [18:36:28.23 C:\hello-world]
        $ mvn clean package
        [INFO] Scanning for projects...
        [WARNING]
        [WARNING] Some problems were encountered while building the effective model for com.juvenxu.mvnbook:hello-world:jar:1.0-SNAPSHOT
        [WARNING] 'build.plugins.plugin.version' for org.apache.maven.plugins:maven-compiler-plugin is missing. @ line 21, column 15
        [WARNING]
        [WARNING] It is highly recommended to fix these problems because they threaten the stability of your build.
        [WARNING]
        [WARNING] For this reason, future Maven versions might no longer support building such malformed projects.
        [WARNING]
        [INFO]
        [INFO] ------------------------------------------------------------------------
        [INFO] Building Maven Hello World Project 1.0-SNAPSHOT
        [INFO] ------------------------------------------------------------------------
        [INFO]
        [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ hello-world ---
        [INFO] Deleting C:\Marslo\Study\Codes\Maven\hello-world\target
        [INFO]
        [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ hello-world ---
        [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
        [INFO] skip non existing resourceDirectory C:\Marslo\Study\Codes\Maven\hello-world\src\main\resources
        [INFO]
        [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ hello-world ---
        [INFO] Changes detected - recompiling the module!
        [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
        [INFO] Compiling 1 source file to C:\Marslo\Study\Codes\Maven\hello-world\target\classes
        [INFO]
        [INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ hello-world ---
        [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
        [INFO] skip non existing resourceDirectory C:\Marslo\Study\Codes\Maven\hello-world\src\test\resources
        [INFO]
        [INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ hello-world ---
        [INFO] Changes detected - recompiling the module!
        [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
        [INFO] Compiling 1 source file to C:\Marslo\Study\Codes\Maven\hello-world\target\test-classes
        [INFO]
        [INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ hello-world ---
        [INFO] Surefire report directory: C:\Marslo\Study\Codes\Maven\hello-world\target\surefire-reports

        -------------------------------------------------------
         T E S T S
        -------------------------------------------------------
        Running com.juvenxu.mvnbook.helloworld.HelloWorldTest
        Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.06 sec

        Results :

        Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

        [INFO]
        [INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ hello-world ---
        [INFO] Building jar: C:\Marslo\Study\Codes\Maven\hello-world\target\hello-world-1.0-SNAPSHOT.jar
        [INFO] ------------------------------------------------------------------------
        [INFO] BUILD SUCCESS
        [INFO] ------------------------------------------------------------------------
        [INFO] Total time: 5.571 s
        [INFO] Finished at: 2014-11-28T18:36:41+08:00
        [INFO] Final Memory: 15M/201M
        [INFO] ------------------------------------------------------------------------
