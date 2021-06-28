# NTU Class Crawler

## Introduction

This is a program that can crawl data of classes in next semester from
"classroom management system(上課教室看板)". With this program, you can arrange your classes before they come out at NTU online. While the information is not quite
complete on the website, it is still a useful and helpful tool if you want to
organize the curriculum for next semester in advance. The reference link is
http://gra206.aca.ntu.edu.tw/classrm/index.php/acarm/webcr-use1-new.
<img src="./sample.gif">

## Environment
<a target="_blank" href="https://www.python.org/downloads/" title="Python version"><img src="https://img.shields.io/badge/python-%3E=_3.7-green.svg"></a> and the following libraries are required.


> <img src="https://img.shields.io/badge/python-requests %7C beautifulSoup4 %7C pandas %7C argparse-blue">


## Optional Arguments
```
optional arguments:
  -h, --help            show this help message and exit
  --semester SEMESTER   Select the semester you want to query
  --delay-time DELAY    Set the delay time between each request
  -p PAGE, --page PAGE  Assign the maximum page of each day.
  -s [SAVE], --save [SAVE]
                        Store the result. You can specify your filename.
                        Please use .xls or .xlsx as filename extension.
  -b {1,2,3,4,5,6,7,8,9,A,B,共同,普通,新生,綜合,博雅,%}
                        Specify the building you want to query.
                        If the building belongs to a college(ex:College of Electrical Engineering and Computer Science),
                        use the code of that college(ex:9),or simply type the name of the building(ex:博雅).
                        The percentage sign means search for all buildings.
                        The default is set as 9.
  --search-opt SEARCHOPT

                        Comma separated values to specifiy search options e.g. "Title=積體電路,Classroom=電二"
                        The avaliable args include:
                            "Id": Curriculum Identity Number
                            "Class": The class number. If the course is teached by only one teacher, it is set to 00
                            "Title": Course title
                            "Instructor": Teacher name
                            "Classroom": Schedule Classroom 
                            "Time": The time of course

                        For example, if you type "--search-opt Title=積體電路,Classroom=電二", you may get the following result:
                                    Id Class        Title Instructor Classroom    Time
                        0  943U0010    00       積體電路測試        李建模     電二146  二2,3,4
                        1  921U9590    00  電力電子與積體電路控制        陳景然     電二225  二7,8,9
                        2  943U0120    00     射頻積體電路設計        陳怡然     電二104  三2,3,4
                        3  90140500    00       積體電路設計        盧奕璋     電二229  三7,8,9
                        4  942U0120    00     微波積體電路專題        林坤佑     電二101  四7,8,9


```
You can view all help message by typing
```
python3 crawl.py -h
```
## Examples
> The default of the building is set as 9 (EECS). Remener to specify the -b option.

If you want to find the class whose name is 機器學習 in EECS and store the result to excel with filename <code>ML.xls</code>, you can use
```
python3 crawl.py --search-opt Title=機器學習 --save ML.xls -b 9 --semester 1101
```
or maybe you just want to find the classes teached in Bioresources and Agriculture college, and save it locally. You can just type
```
python3 crawl.py -b 6 --save Agri.xlsx --semester 1101
```
A common way of using this program is to download all of the courses into a xlsx file, and you can search directly in the xlsx file locally.
(It may take a while to execute it, since you want to go through all of the pages in the website.)
```
python3 crawl.py -b % --save course.xlsx --semester 1101
```

