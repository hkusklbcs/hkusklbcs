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

.. code-block:: Bash
  declare -A array
  array["sub-001"]="MDD"
  array["sub-002"]="Healthy"
  array["sub-003"]="MDD"
  echo ${array["sub-001"]}
  # MDD
  sub="sub-002"
  echo ${array[$sub]}
  # Healthy
  sub="sub-004"
  echo ${array[$sub]}
  # 
  echo ${array[$sub]-undefined}
  # undefined

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

  if-then-fi

  if-then-else-fi

  if-then-elif-fi

  if-then-elif-else-fi

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

  for var in item{1..3}; do
    echo $var
  done

