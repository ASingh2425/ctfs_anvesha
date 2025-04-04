The challenge directory contains a Dockerfile that describes the challenge and any challenge files. 
challenge.yaml is the main configuration file. I tried using it to change settings like the name and namespace of the challenge, 
the exposed ports, the proof-of-work difficulty etc. For documentation on the available fields, ran kubectl explain challenge and kubectl explain challenge.spec..to get explanation
A Docker image is built from the challenge directory.
Edited challenge/Dockerfile to change the commandline or the files you want to include.
challenge/chal.c worked for me
