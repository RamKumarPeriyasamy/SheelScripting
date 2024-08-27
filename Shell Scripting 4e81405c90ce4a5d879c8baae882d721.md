# Shell Scripting

```bash
#! /bin/bash
echo "Hello World"
```

  Hello World

```bash
echo $BASH
echo $BASH_VERSION
echo $HOME
echo $PWD
   
#/bin/bash
#5.1.16(1)-release
#/home/hexriot
#/mnt/c/Users/hexrd
```

```bash
namw=Mark
10Val=10
echo The name is $namw
echo the  value is $10Val

#The name is Mark
#the value is 0Val
```

```bash

namw=Mark
Val=10
echo The name is $namw*
 echo the  value is $Val 
 
#The name is Mark
#the value is 10
```

```bash
echo "Enter Name : "
read name
echo "Enterd Name : $name "

#Enter Name :
#ram
#Enterd Name : ram
```

```bash
echo "Enter Name : "
read name1 name2 name3 
echo "Enterd Name : $name1 , $name2 , $name3 "
 
#Enter Name :
#ram ,kumar , periyasamy
#Enterd Name : ram , ,kumar , , periyasamy
```

```bash
read -p "UserName : " user_var
read -sp "password : " pass_var  
echo
echo "UserName : $user_var"
echo "password : $pass_var"

#UserName : ramkumar
#password :
#UserName : ramkumar
#password : periyasamy
```

```bash
echo "Enter Name  : "
read -a names
echo "Names : ${names[0]}, ${names[1]}"

#Name  :
#raM KUMAR
#Names : raM, KUMAR

```

```bash
echo "Enter Name : "
read 
echo "Names : $REPLY"

#Enter Name :
#ram kuamr
#Names : ram kuamr
```

```bash
echo $0 $1 $2 $3 ' > echo $0 $1 $2 $3 ' 
args="$@"
#echo ${args[0]} ${args[1]} ${args[2]}
echo $@
echo $#
 
#: sh hello.sh ra umar peri

#hello.sh ra umar peri  > echo $0 $1 $2 $3
#ra umar peri
#3

#disclaimer: too mush error 
```

## IF Statement

```bash
**#SYNTAX:**

if [condition]
then 
   condition
 fi

-----------------------
**#equals :** 

count=10

if [ $count -eq 9 ]
then 
  echo"condition is true"
fi
   
   
count=10

if [ $count -eq 10 ]
then 
  echo"condition is true"
fi
 #condition is true
 
------------------

#not equals
 
count=10
if [ $count -ne 10 ]
then 
  echo"condition is true"
fi
  # condition is true
----------------------
if else  
  
word=a  
  if [[ $word == "a" ]]
#then 
    "condition is true"
else
  echo "conndition is false"
fi 

 # ./hello.sh
# condition is  true
 
 
 word=b
if [[ $word == "b" ]]; then 
   echo "condition is b true"
elif [[ $word == "a" ]]; then
    echo "condition is a true"
else
   echo "condition is false"
fi 

# ./hello.sh
# condition is b true

```

```bash
**#its for file search**

-e "Enter the file name : \c"
read file_name

if [ -e $file_name ]
then
 echo "$file_name found"
else
 echo "$file_name not found"
fi 

#Enter the file name : dior
#dior found
--------------
#its  for directory 

echo -e "Enter the file name : \c"
read file_name

if [ -d $file_name ]
then
 echo "$file_name found"
else
 echo "$file_name not found"
fi 
---------------

#-b for Block files is a binary file like photo 
#-c for characteristic file 

----------------
#if the file is empty or not use -s 

echo -e "Enter the file name : \c"
read file_name

if [ -s $file_name ]
then
 echo "$file_name empty"
else
 echo "$file_name not empty"
fi 
-----------------
```

```bash
**#case satement**
**#SYNTAX**

case expression in
  pattern1 )
      statements ;;
  pattern2 )
      statements ;;
  ...
esac

---------------------------

vehicle=$1

case $vehicle in
   "car" )
       echo "rent of the $vehicle is 100 dolllar" ;;
    "van" )
       echo "rent of the $vehicle is 150 dolllar" ;;
    "truck" )
       echo "rent of the $vehicle is 200 dolllar" ;;
    "bus" )
       echo "rent of the $vehicle is 500 dolllar" ;;
    *)
        echo "unknown " ;;
esac

#./hello.sh car
# rent of the car is 100 dolllar
#./hello.sh van
# rent of the van is 150 dolllar
```

```bash
**#array setup**
os=('windows' 'ubuntu' 'ios')

 echo  "${os[@]}"
 echo "${os[2]}"
 echo "${!os[@]}"
 echo "${#os[@]}"
 
 #./hello.sh 
#windows ubuntu ios mac
#ios
#0 1 2
#3
 
os=('windows' 'ubuntu' 'ios')
os[3]='mac'
 echo  "${os[@]}"
 echo "${os[2]}"
 echo "${!os[@]}"
 echo "${#os[@]}"

#./hello.sh 
#windows ubuntu ios mac
#ios
#0 1 2 3
#4

#remove array
os=('windows' 'ubuntu' 'ios')
os[3]='mac'
 unset os[2]
 echo  "${os[@]}"
 echo "${os[1]}"
 echo "${!os[@]}"
 echo "${#os[@]}"
 
#windows ubuntu mac
#ubuntu
#0 1 3
#3

-------------
Array index number/place change

os=('windows' 'ubuntu' 'ios')
os[6]='mac'

 echo  "${os[@]}"
 echo "${os[1]}"
 echo "${!os[@]}"
 echo "${#os[@]}"
 
 #windows ubuntu mac
#ubuntu
#0 1 2 6
#4
```

```bash
**#While Loop SYNTAX**

while [ condition ]
 do
      command1
      command2
      command3
done

-------------------

n=1

while [ $n -le 10 ]
do 
    echo "$n"
    n=$(( n+1 ))
done

# ./hello.sh
1
2
3
4
5
6
7
8
9
10
------------------
n=1

while [ $n -le 10 ]
do 
    echo "$n"
    n=$(( ++n ))
done 

# ./hello.sh
1
2
3
4
5
6
7
8
9
10
-------------------

```

```bash
**cat hello.sh** | while read p
do  
   echo $p
done 

cat hello.sh 
this an read the file content one variable and then print it.

----------------
ifs - internel felds seprator

while IFS= read -r line 
do 
   echo $line
done  <  hello.sh

```

```bash
**#UNTIL LOOPS :
#SYNTAX** :

until [ condition ]
do 
   command1
   command2
   ......
   ......
   commandN
done   

when until condion fail then only executed
------------
# greater than equal to
n=1

until [ $n -ge 10 ]
do 
  echo $n
  n=$(( n+1 ))
done

 #./hello.sh
1
2
3
4
5
6
7
8
9

----------------

#greater than

n=1

until [ $n -gt 10 ]
do 
  echo $n
  n=$(( n+1 ))
done

 #./hello.sh
1
2
3
4
5
6
7
8
9

```

```bash
**#for loop 
#syntax**

for VARIABLE in 1 2 3 4 5 .. N
do
    command1
    command2
    commandN
done

#or

for VARIABLE in file1 file2 file3
do
    command1 on $VARIABLE
    command2
    commandN
done

#or

for OUTPUT in $(Linux-Or-Unix-Command-Here)
do
    command1 on $OUTPUT
    command2 on $OUTPUT
    commandN
done

#or

for (( EXP1; EXP2; EXP3 ))
do
    command1
    command2
    command3
done

------------------

for i in {0..10..2} #{start .. end .. increment}
do 
    echo $i
done

#./hello.sh
0
2
4
6
8
10

for i in {1..10..2} #{start .. end .. increment}
do 
    echo $i
done

#./hello.sh
1
3
5
7
9

------------------

echo ${BASH_VERSION}
for (( i=0; i<5; i++ )) #{start .. end .. increment}
do 
    echo $i
done

#./hello.sh
5.1.16(1)-release
0
1
2
3
4
```

```bash
**#Age setup by IF ELSE**

age=19

if [ "$age" -gt 18 -a "$age " -lt 30 ]
then 
  echo "valid age"
  else
  echo "invalid age"
fi

# -a flag is an and operator
# ./hello.sh
# valid age

age=19

if [ "$age" -gt 18 -a "$age " -lt 30 ]
then 
  echo "valid age"
  else
  echo "invalid age"
fi

# ./hello.sh
# invalid age
					

# another method

age=19

if [[ "$age" -gt 18 && "$age " -lt 30 ]]
then 
  echo "valid age"
  else
  echo "invalid age"
fi

# we use in these method (&&) by using [[]] by these
```

```bash
**#sum of numbers
#simple add,sub,mul, division,modules**

num1=5
num2=30

echo $(( num1 + num2 ))
echo $(( num1 - num2 ))
echo $(( num1 * num2 ))
echo $(( num1 / num2 ))
echo $(( num1 % num2 ))

#./hello.sh
35
-25
150
0
5
```

```bash
**#permission file for write an execute**

echo -e "Enter the file name : \c"
read file_name

if [ -f $file_name ]
then
     if [ -w $file_name ]
     then
        echo "type some text data. To quit press ctrl+d"
        cat >> $file_name
     else
        echo "TYhe file does not have such permissions"
     fi
else
 echo "$file_name not exists"
fi

#touch distac 
#/hello.sh
#Enter the file name : distac
#type some text data. To quit press ctrl+d
#ram kumar periyasamy

#chmod 555 distac 
#./hello.sh
#Enter the file name : distac
#TYhe file does not have such permissions

```

```bash
**#SYNTAX for SELECT LOOP**

select varName in list
do
    command1
    command2
    ......
    ......
    commandN
done

#or 

select varName in list
do
	case $varName in
		pattern1)
			command1;;
		pattern2)
			command2;;
		pattern1)
			command3;;
		*)
			echo "Error select option 1..3";;
	esac			
done

---------------

select name in ram raju sam john
do
   echo "$name selected"
done

#./hello.sh
1) ram
2) raju
3) sam
4) john
>>   

-----------------

select name in ram raju sam john
do
   case $name in
   ram)
   echo ram selected
   ;;
   raju)
   echo raju selected
   ;;
   sam)
   echo sam selected
   ;;
   john)
   echo john selected
   ;;
   *)
   echo "Error please provide th no. btw 1..4"
   esac

done

#./hello.sh
1) ram
2) raju
3) sam
4) john
>> 1
ram selected
>> 2
raju selected
>> 3
sam selected
>> 4
john selected
>> 5
Error please provide th no. btw 1..4
>> 6
Error please provide th no. btw 1..4
>>
```

```bash
**#BREAK STATEMENT**

for (( i=1; i<=10 ; i++))
do
      if [ $i -gt 5 ]
      then 
         break
      fi
      echo "$i"
done

#./hello.sh
1
2
3
4
5

```

```bash
**#Functions Command**
function name() {
   commands
}
name() {
   commands
}
------------

function print(){
   echo $1
}
quit() {
   exit
}

print hello
echo "foo"
quit

#./hello.sh
hello
foo

---------- 
```

```bash
**#function keyWord**

function print(){
   local name=$1
   echo "the name is $name"
}

name="tom"

echo "the name is $name : Before"

print Max

echo "the name is $name : After"

#./hello.sh
#the name is tom : Before
#the name is Max
#the name is tom : After

function print(){
   
name=$1
   echo "the name is $name"
}

name="tom"

echo "the name is $name : Before"

print Max

echo "the name is $name : After"

#)./hello.sh
#the name is tom : Before
#the name is Max
#the name is Max : After
```

```bash
**#File exist command**

usage() {
   echo "you need provide an argument : "
   echo "usage : $0 file_name"
}

is_file_exist() {
   local file="$1"
   [[ -f "$file" ]] && return 0 || return 1
} 

[[ $# -eq 0 ]] && usage

if ( is_file_exist "$1" )
then 
    echo "file found"
else
   echo "file not found"
fi

# ./hello.sh
you need provide an argument :
usage : ./hello.sh file_name
file not found
(error message )

#./hello.sh  file1.txt
file found

# ./hello.sh  dior
file found

# ./hello.sh  name.txt
file not found
```

```bash
**#READONLY COMMAND**

var=31

readonly var

var=50

echo "var => $var"

hello() {
   echo "hello world again"
}

**#readolny key only read the var 
#./hello.sh**
./hello.sh: line 220: var: readonly variable
var => 31

-------------

var=31

readonly var

var=50

echo "var => $var"

readonly -f hello

hello() {
   echo "hello world again"
}

readonly

#They give a error msg.
#./hello.sh
./hello.sh: line 220: var: readonly variable
var => 31
./hello.sh: line 224: readonly: hello: not a function
declare -r BASHOPTS="checkwinsize:cmdhist:complete_fullquote:extquote:force_fignore:globasciiranges:hostcomplete:interactive_comments:progcomp:promptvars:sourcepath"
declare -ar BASH_VERSINFO=([0]="5" [1]="1" [2]="16" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
declare -ir EUID="1000"
declare -ir PPID="18618"
declare -r SHELLOPTS="braceexpand:hashall:interactive-comments"
declare -ir UID="1000"
declare -r var="31"
```

```bash
**#this file for deleting and pid finding purpuse**

file=/mnt/c/Users/hexrd/file1.txt
trap "rm -f $file && echo file deleted; exit" 0 2 15

echo "pid is $$"
while (( COUNT < 10 ))
do
   sleep 10
   (( COUNT ++ ))
   echo $COUNT
done
exit 0

# ./hello.sh
pid is 193287
1
2
3
4
5
6
7
^Cfile deleted
file deleted

# bash -x ./hello.sh
+ file=/mnt/c/Users/hexrd/file1.txt
+ trap 'rm -f /mnt/c/Users/hexrd/file1.txt && echo file deleted; exit' 0 2 15
+ echo 'pid is 194780'
pid is 194780
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 1
1
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 2
2
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 3
3
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 4
4
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 5
5
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 6
6
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 7
7
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 8
8
+ ((  COUNT < 10  ))
+ sleep 10
+ ((  COUNT ++  ))
+ echo 9
9
+ ((  COUNT < 10  ))
+ sleep 10
^C++ rm -f /mnt/c/Users/hexrd/file1.txt
++ echo file deleted
file deleted
++ exit
+ rm -f /mnt/c/Users/hexrd/file1.txt
+ echo file deleted
file deleted
+ exit
```