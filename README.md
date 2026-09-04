# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 




# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "my-folder"

mkdir my-folder

<img width="497" height="150" alt="Screenshot 2026-09-03 091815" src="https://github.com/user-attachments/assets/6184987a-6485-414c-a837-d7b299c83323" />

## COMMAND AND OUTPUT

Remove the directory "my-folder"


rmdir my-folder


<img width="485" height="146" alt="Screenshot 2026-09-03 091834" src="https://github.com/user-attachments/assets/f5058352-d24c-4f99-bbc6-d9c79dd4c97a" />

## COMMAND AND OUTPUT


Create the file Rose.txt



COPY CON Rose.txt
A clock in a office can never get stolen
Too many employees watch it all the time
^Z
1 file(s) copied
dir Rose.txt

<img width="710" height="375" alt="Screenshot 2026-09-03 091248" src="https://github.com/user-attachments/assets/b5d365d9-ec82-4a72-b2a4-14c4bb35505e" />


## COMMAND AND OUTPUT


Create the file hello.txt using echo and redirection
echo “hello world” > hello.txt
type hello.txt


<img width="623" height="182" alt="Screenshot 2026-09-03 091329" src="https://github.com/user-attachments/assets/235de150-cdc8-4f73-91b6-bd7fbfbe93ca" />

## COMMAND AND OUTPUT

Copy the file hello.txt into the file hello1.txt

copy hello.txt hello1.txt

<img width="683" height="321" alt="Screenshot 2026-09-03 091639" src="https://github.com/user-attachments/assets/6cae7567-8c87-46e8-85c0-c7aa7878845e" />


## COMMAND AND OUTPUT

Remove the file hello1.txt
del hello1.txt


<img width="490" height="196" alt="Screenshot 2026-09-03 091543" src="https://github.com/user-attachments/assets/743e8a4b-ed98-4403-b16a-2dd4152e8708" />


## COMMAND AND OUTPUT

List out the file hello1.txt in the current directory

dir hello1.txt

<img width="490" height="196" alt="Screenshot 2026-09-03 091543" src="https://github.com/user-attachments/assets/dbc49e1e-dbba-4e5f-9adf-630297d7c230" />



## COMMAND AND OUTPUT

List out all the associated file extensions 
assoc | more

<img width="585" height="703" alt="Screenshot 2026-09-03 091527" src="https://github.com/user-attachments/assets/32955357-ad57-4848-b5e3-a5436eab58e7" />

## COMMAND AND OUTPUT


Compare the file hello.txt and rose.txt
fc hello.txt Rose.txt

<img width="610" height="247" alt="Screenshot 2026-09-03 091503" src="https://github.com/user-attachments/assets/91752574-62f5-4802-9b37-590f85ab66f6" />


## COMMAND AND OUTPUT

## Exercise 2: Advanced Batch Scripting
Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".

BATCH SCRIPT
Open Notepad with filename 1.bat and type the following batch script
@echo off
set name=John
echo Hello, %name%!
pause







## OUTPUT

<img width="511" height="147" alt="Screenshot 2026-09-03 092218" src="https://github.com/user-attachments/assets/c8431d36-b788-4a87-a9bb-1f04d2a3a844" />


Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.

@echo off
:main
set /p number=Enter a number: 
rem Calculate remainder when divided by 2
set /a remainder=%number% %% 2
if %remainder%==1 (
    echo %number% is an odd number.
) else (
    echo %number% is not an odd number.
)
:choice
set /p continue=Do you want to check another number? (Y/N): 
if /i "%continue%"=="Y" goto main
if /i "%continue%"=="N" goto end
echo Invalid choice, please enter Y or N.
goto choice
:end
echo Thank you for using the odd number checker!
pause


## OUTPUT

<img width="720" height="202" alt="Screenshot 2026-09-03 092313" src="https://github.com/user-attachments/assets/7c66dd8f-18d4-4ba2-99ee-5d25c38282f2" />



Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.

@echo off
for %%i in (1 2 3 4 5) do (
    echo Number: %%i
)
pause



## OUTPUT

<img width="598" height="301" alt="Screenshot 2026-09-03 092337" src="https://github.com/user-attachments/assets/0b5384c8-4705-4857-b153-3aed705b05b9" />



Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):

@echo off
if exist sample.txt (
    echo sample.txt exists.
) else (
    echo sample.txt does not exist.
)
pause


## OUTPUT

<img width="691" height="207" alt="Screenshot 2026-09-03 092407" src="https://github.com/user-attachments/assets/42b01b3e-b12f-4109-b6c8-64c122c06405" />


Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.

@echo off
:menu
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
set /p choice=Choose an option: 
if "%choice%"=="1" goto hello
if "%choice%"=="2" goto createfile
if "%choice%"=="3" goto end

:hello
echo Hello, World!
goto menu

:createfile
echo Creating a file...
echo This is a new file > newfile.txt
goto menu
:end
echo Goodbye!
pause


## OUTPUT

<img width="422" height="432" alt="Screenshot 2026-09-03 092505" src="https://github.com/user-attachments/assets/c8028dad-0dc0-45d5-b943-6b5ff8b5dfd9" />


# RESULT:
The commands/batch files are executed successfully.

