BASH Scripting Examples
=======================

I will go into the details later. Below are some usage examples. I hope it looks intuitive.

Variables
*********

Assignment

.. code-block:: Bash

  var="apple"
  var=1

Replacement

.. code-block:: Bash

  var="I like apple!"
  var=${var/apple/banana}
  echo "$var"
  # I like banana!

Arrays
******

Simple Array


.. code-block:: Bash

  unset array # Remove the variable
  array=("apple" "banana" "cherry" "durian")
  echo ${array[0]} # first element begins with 0
  # apple
  echo ${array[@]} # all elements
  # apple banana cherry durian
  echo ${#array[@]} # number of elements
  # 4 
  echo ${!array[@]} # keys to array
  # 0 1 2 3
  array[7]=fish
  echo ${!array[@]}
  # 0 1 2 3 7
  unset array[3] # Remove the item #3
  echo ${array[@]}
  # apple banana cherry fish
  echo ${!array[@]}
  # 0 1 2 7
  echo ${#array[@]}
  # 4
  for i in ${!array[@]}; do
    echo "key = $i; value = ${array[$i]}"
  done
  # key = 0; value = apple
  # key = 1; value = banana
  # key = 2; value = cherry
  # key = 7; value = fish
  unset array

Associative Array

.. code-block:: Bash

  declare -A array
  
  array["sub-001"]="MDD"
  array["sub-002"]="Healthy"
  array["sub-003"]="MDD"
  echo ${array["sub-001"]}
  ``MDD``
  sub="sub-002"
  echo ${array[$sub]}
  ``Healthy``
  sub="sub-004"
  echo ${array[$sub]}
  `` `` (empty)
  echo ${array[$sub]-undefined}
  ``undefined``
  
  
  array="hello"
  declare -A array
  ``bash: declare: array: cannot convert indexed to associative array``
  unset array
  declare -A array
  `` `` (This will return no error)  


Try different combinations. You will know how to manipulate the array. This is important for scripting.

Arithmetics
***********

.. code-block:: Bash

  var=$((5+5))
  echo $var
  # 10
  var2=$((var+10))
  echo $var2
  # 20
  echo $((var))
  # 10
  echo $((var+2))
  # 12
  echo $((var-2))
  # 8
  echo $((var*2))
  # 20
  echo $((var/2))
  # 5
  echo $((var%3))
  # 1
  

Control Structures
******************

if-statements

.. code-block:: Bash

  ### if-then ###
  var1=a
  if [ "$var1" = a ]; then
    echo "Is a!"
  fi
  # Is a!
  
  ### if-then-else ###
  var1=b
  if [ "$var1" = a ]; then
    echo "Is a!"
  else
    echo "Is NOT a!"
  fi

  ### if-then-elif ###
  var1=c
  if [ "$var1" = a ]; then
    echo "Is a!"
  elif [ "$var1" = b ]; then
    echo "Is b!"
  else
    echo "Not a/b..."
  fi

case-statements

.. code-block:: Bash

  case var...


testing conditions (file existence)

.. code-block:: Bash

  [ -f file ]
  [ -d directory ]
  [ -e fileOrFolder ]

testing conditions (numerical comparison)

.. code-block:: Bash

  [ $var1 -lt $var2 ]
  [ $var1 -le $var2 ]
  [ $var1 -gt $var2 ]
  [ $var1 -ge $var2 ]
  [ $var1 -ne $var2 ]

testing conditions (string comparison)

.. code-block:: Bash

  [ $var1 = $var2 ]     # This is dangerous, if any of the variables are not defined, it will ends up with error.
  [ "$var1" = "$var2" ] # This is better.

testing conditions (regular expression comparison)

.. code-block:: Bash

  [[ "$var1" =~ "a.*b" ]] # You will need to check the Regular Expression documentations. It's a powerful tool.

testing conditions (and or not)

.. code-block:: Bash

  [ "$var" = "apple" ] && [ "$var" = "orange" ] # AND
  [ "$var" = "apple" ] || [ "$var" = "orange" ] # OR
  ! [ "$var" = "apple" ] && [ "$var" = "orange" ] # Not


Loop
****

.. code-block:: Bash

  for var in item1 item2 item3; do
    echo $var
  done
  # item1
  # item2
  # item3

  for var in sub-00{1..3}; do
    echo $var
  done
  # sub-001
  # sub-002
  # sub-003
  
