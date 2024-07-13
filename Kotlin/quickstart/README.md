# guide about Kotlin
## Installation and setup
1. Install kotlin compiler if NOT installed. (As it is too complicate. See the following Installation section).
2. Ensure that kotlin compiler (i.e. kotlinc) is set to system environment variable PATH  (By default, the directory is "{YOUR_PATH}\kotlinc\bin" that contains file name kotlinc. (Such as "C:\Users\{USERNAME}\.kotlin\kotlinc\bin" ). If NOT set, set it then reboot the device to make the change effect.
3. Install java compiler if NOT installed.
4. Ensure that java compiler (i.e. javac.exe) is set to system environment variable PATH  (By default, the directory is "{YOUR_PATH}\jbr\bin" that contains file name javac.exe. (Such as "C:\Program Files\Android\Android Studio\jbr\bin" ). If NOT set, set it then reboot the device to make the change effect.

## Write your first program, compile, and execute 
1. On text editor (such as VSC).
2. Write code in Kotlin.
3. Save it as .kt file.
4. Compile the .kt file into .jar file.
5. Run the .jar file.

## Example
I create test1.kt in the directory "C:\Users\{USERNAME}\OneDrive\桌面". 
Then I write these code.

      fun main() {
      	println("Hello")
      }

To run these code,

1. I have to open terminal.
2. Change the directory to "C:\Users\{USERNAME}\OneDrive\桌面".
3. To compile test1.kt and create a .jar file (for example test1.jar), I type these command in terminal.

         kotlinc test1.kt -include-runtime -d test1.jar
   
4. Then I run the test1.jar with java by the following command.

         java -jar test1.jar

Then the output will be 
            
      Hello
      
### Code 
      
      fun main() {
      	println("Hello")
      }
      
### Output 

      Hello
      
## NOTES
1. If you have already install Android Studio under the directory "C:\Program Files\Android\Android Studio".
   
By default, java will be installed. Full path of javac.exe will be

       "C:\Program Files\Android\Android Studio\jbr\bin\javac.exe"

## Installation 
### Way 1: For only install the Kotlin compiler
Visit Kotlin Docs with detailed instruction at

https://kotlinlang.org/docs/command-line.html

### Way 2: Install IDE and Kotlin compiler
Since these IDE 

+ IntelliJ IDEA
+ Android Studio
+ JetBrains Fleet 

includes kotlin compiler. 

One ** DON'T ** have to install the compiler.

For more detailed information, visit Kotlin Docs at

+ https://kotlinlang.org/docs/getting-started.html
+ https://kotlinlang.org/docs/command-line.html

## Execute .kt file
### Way 1: With kotlin compiler in terminal
To execute test1.kt file, in terminal, type these command

      kotlinc test1.kt

For more detail about how to compiling kotlin program, visit kotlin docs.

https://kotlinlang.org/docs/command-line.html#create-and-run-an-application

