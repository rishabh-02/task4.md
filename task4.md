<h2 align="center">Task-4</h2>

<details>
  <summary> Summary of Task </summary>
  <ul>
    <br>
    <li> Write a script in Shell.</li>
    <li> This script has been used to download 2 google sheets. </li>
    <li> Both of those Google sheets will have the formate csv file. </li>
    <li> Only the name, Average and Sum columns and their values should be printed. </li>
    <li>After that we get the downloaded seat compaired from our existing seat.</li>
  </ul>
</details>

<details>
<summary> INDEX </summary>
  <ul>
    <br>
    <li> Test cases</li>
    <li> Implementation </li>
    <li> Script </li>
    <li> Log file </li>
    <li> Conclusion </li>
  </ul>
  </details>

<details>
<details>
  <summary> Test Cases </summary>
  
|Test Cases|Test Case Description|Steps Performed| Test Status|Output
|:----:|:-----:|:-----:|:-----:|:-----:|
|Test Case 1| **Already Save Raw Output** <br/> | An output file is already saved which needs to be compressed. | PASS |![](https://github.com/rishabh-02/task3.md/blob/master/screen1.png) <br/> |
|Test Case 2| **When New Output Downloaded** <br/> | Whenever a new output is generated, we go to its path and change it in the script file.| PASS | ![](https://github.com/rishabh-02/task3.md/blob/master/screen2.png) |
|Test Case 3| **Compare Both Output** <br/> | Then we get both the files to be compressed by the diff command. | PASS | ![](https://github.com/rishabh-02/task3.md/blob/master/screen3.png) |
|Test Case 4| **Generate Log** <br/>| After that our log is being generated. |PASS|![](https://github.com/rishabh-02/task3.md/blob/master/screen4.png) |
  </details>
  
  <details>
  <summary> Implementation </summary>
  
We already have an output and when running the script when the new output is downloaded, then compare to it.  What is the difference between the two and their log is generated and we get the difference.
  
  </details>
  
  <details>
  <summary> Script </summary>
  #! /bin/bash

Pwd=`/usr/bin/pwd`          # pwd is Enabled to source the working directory of config file at the beginning

source $Pwd/script.conf     # used to source the config file to the script and $Pwd will redirect the exact path
$TOUCH $Pwd/valuation.log   # log file has been created to the directory
#-----------------------------------------------------------------------------------------------------------------------------------------
func(){ if [[ $? -ne 0 ]]; then $ECHO "Failure at $1">> $Pwd/valuation.log
        exit
    else
            $ECHO $date $Pwd $0 $2 $3 $4
            fi }                                 	#function 'func()' will match the condition if commands execute or not and give the logs                                                                                  failure an exit if condition of execution fails.
                                                        #if function passes then it will generate output to logs folder from wherever it is called


#-----------------------------------------------------------------------------------------------------------------------------------------
$ECHO $date $Pwd  " INITIALISING $0">> $Pwd/valuation.log                                          #storing logs in specified >> filename

$DIFF -y /home/rishabh/Documents/Rishabh-Script/data/Output1.csv /home/rishabh/Documents/Rishabh-Script/data2/Output_of_sheet1.csv
 if [[ $? -eq 0 ]];
 then 
	 $ECHO "PASS: Match Found" 
	 func $LINENO "[SUCCESS] Output_of_sheet1 Match found Succesfully">> $Pwd/valuation.log
 else
	 $ECHO "FAIL: No Match Found"
	 func $LINENO "[FAILED] Output_of_sheet1 Match Not Found ">> $Pwd/valuation.log
 fi

#-----------------------------------------------------------------------------------------------------------------------------------------

$DIFF -y /home/rishabh/Documents/Rishabh-Script/data/Output2.csv /home/rishabh/Documents/Rishabh-Script/data2/Output_of_sheet2.csv
 if [[ $? -eq 0 ]];
 then
         $ECHO "PASS: Match Found"
	 func $LINENO "[SUCCESS] Output_of_sheet2 Match found Succesfully">> $Pwd/valuation.log
 else
         $ECHO "FAIL: No Match Found"
	 func $LINENO "[FAILED] Output_of_sheet2 Match Not Found ">> $Pwd/valuation.log
 
 fi
func $LINENO "[SUCCESS] Output generated to terminal ">> $Pwd/valuation.log     #storing logs in specified >> filename
func $LINENO "[EXITING "$0" ]">> $Pwd/valuation.log                             #storing logs in specified >> filename                                                                                                                                                                                                                                   
  </details>
  
 <details>
  <summary> Configuration file </summary>
  
#Below are the list of path variables declared:
MKDIR=/usr/bin/mkdir           #Creating a Directory
RENAME=/usr/bin/mv             #Moving or Renaming file or Directory
ECHO=/usr/bin/echo             #To Print
SHOW=/usr/bin/cat              #To show content of Files 
DOWNLOAD=/usr/bin/wget         #Non-Interactive network downloader
MATCH=/usr/bin/grep            #To search or match the content
TRAN=/usr/bin/tr               #To traverse or delete
COUNT=/usr/bin/wc              #To Count
SCAN=/usr/bin/awk              #To Extract the data from files
date=`/usr/bin/date`           #To Print the Date and Time
Pwd=`/usr/bin/pwd`             #To print working directory
REM=/usr/bin/rm                #To remove the file
TOUCH=/usr/bin/touch
DIFF=/usr/bin/diff
#URLs used to download both google spreadsheet files through public link exporting the data to csv:

URL1='https://docs.google.com/spreadsheets/d/e/2PACX-1vTrNldUZStbLCL-Q9Le9ilWrWxR1XW5N4zOzpBbM4aBEsgp2wheS7ioOx0yQ8a_zZuxvw4fXkwYH-Mh/pub?output=csv'

URL2='https://docs.google.com/spreadsheets/d/e/2PACX-1vRc3-RATBQ0U-XYPwb8uRHs0sMwJspqnspJxWFPXVz_pF0NA2QTFA-rkmPsRjMOlF_xPdpwBRjYOkhK/pub?output=csv'

#Please donot change the url as the script is designed to Extract values with similar spreadsheets to that of Url only.

  </details>

<details>
<summary> Log file </summary>
  
Wednesday 19 May 2021 10:23:17 AM IST /home/rishabh/Documents/Rishabh-Script  INITIALISING ./valution.sh
Wednesday 19 May 2021 10:23:17 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [FAILED] Output_of_sheet1 Match Not Found
Wednesday 19 May 2021 10:23:17 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [SUCCESS] Output_of_sheet2 Match found Succesfully
Wednesday 19 May 2021 10:23:17 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [SUCCESS] Output generated to terminal
Wednesday 19 May 2021 10:23:17 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [EXITING ./valution.sh ]
Wednesday 19 May 2021 10:24:40 AM IST /home/rishabh/Documents/Rishabh-Script  INITIALISING ./valution.sh
Wednesday 19 May 2021 10:24:40 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [SUCCESS] Output_of_sheet1 Match found Succesfully
Wednesday 19 May 2021 10:24:40 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [SUCCESS] Output_of_sheet2 Match found Succesfully
Wednesday 19 May 2021 10:24:40 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [SUCCESS] Output generated to terminal
Wednesday 19 May 2021 10:24:40 AM IST /home/rishabh/Documents/Rishabh-Script ./valution.sh [EXITING ./valution.sh ]

  </details>


<details>
<summary> Conclusion</summary>
  I want to share that I have learned alots of new things while working in this script which is working successfully.
</details>
  
  ```
     Thank You
```
