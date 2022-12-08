# Exam_2420

## Part 1

To update most of the software on your Ubuntu OS, you can run these commands:

    sudo apt update
    sudo apt upgrade

## Part 2

I first changed all the `eco`'s to `echo`

I used `/` to search `eco` navigated to past the c and then entered `a` to go into insert mode and entered `h`.

Next I used `/` to search for `V`, entered `r` to enter replace mode and entered `C` to replace the `V` with `C`

Next I searched for `numb` using `/` and deleted the word with `x` and entered `digit` with `a`

![Part 2](./images/part2.png)

## Part 3

All the parts I found in the journalctl man page

![boot](./images/part3_boot.png)

![output](./images/part3_output.png)

![json_pretty](./images/part3_json_pretty.png)

![priority](./images/part3_priority.png)

I found all of these by searching with the `/` followed by the word I was looking for

This is the working command: sudo journalctl -p "warning" -b -o json-pretty

![part3_success](./images/part3_success.png)

## Part 4

Script to get all regular users and print the output

    1 #!/bin/bash
    2
    3 # assign file to a variable
    4 reg_users_file="/etc/passwd"
    5
    6 echo "Regular users on the system are:"
    7
    8 # search file for users with UID between 1000 and 5000
    9 awk -F: '($3 >= 1000 && $3 <= 5000) {print $1, $3 "/", $7}' $reg_users_file
    10
    11 echo "Users currently logged in are:"
    12
    13 # find users currently logged in
    14 who | awk '{print $1}' >/etc/motd

## Part 5

Service file to that runs the previous script

    [Unit]
    Description=Finds all of the regular users on a system and prints them to the motd file.

    [Service]
    Type=oneshot
    ExecStart=/home/vagrant/bin/get_users

    [Install]
    WantedBy=multi-user.target

![part5_success](./images/part5_success.png)





