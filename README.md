# Eurecom-fuzzV1.0
Eurecom-fuzz Version1.0
Eurecom-fuzz is a set of bash scripts written by Mohamed NJEH & Ala TARHOUNI as a part of an academic Project at EURECOM.
The tool permits its user to launch multiple fuzzing tasks at the same time using different Fuzzers and on different binaries
and different sets of data. The fuzzers used are AFLPlusPlus, AFLGo, AFLSmart and Eclipser.
In order to set up the tools few setps are to be followed. First make a directory at ~/shared/ to be the shared folder between the host and 
docker containers where you put inputs in ~/shared/input and output in ~/shared/output and the binary directly in ~/shared/Binary
To see help of the tool just type ./eurecom-fuzz  and to see the help of each fuzzer just type the equivalent tag (eg ./eurecom-fuzz -Ec for eclipser or ./eurecom-fuzz -As for AFLSMART)
Please note that the shared folder inside the containers is located in /var/Eurecom so you can put it directly or do the ~/shared/ and the tool will parse it correctly.
NB: Please follow the order of the fuzzers indicated above in ./eurecom-fuzz

build dockerfiles accordingdly 
in ~/project/AFLPLUPLUS docker build -t aflpluplus:v0.2 .
in ~/project/AFLGO docker build -t go:v0.2 .
in ~/project/AFLSMART docker build -t aflsmart:v0.2 . 
in ~/project/Eclipser docker build -t eclipser:v0.2 .


Voila You're Ready to go!
HAVE FUN!
GO EURECOM!
