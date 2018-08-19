# Makefile 
# author: Tian Xia
# org: Infolab@tamu
# date: Aug 19, 2015

CC=riscv64-unknown-linux-gnu-g++

all : twitterClient

#libcurl : 
#		cd ../libtwitcurl && make install 
#		cd ../twitterClient
	

twitterClient : twitterClient.cpp
	$(CC) twitterClient.cpp -I./include/ -L/home/centos/twitcurl/libtwitcurl/libtwitcurl.so.1.0 -o twitterClient



clean : 
		rm twitterClient
		cd ../libtwitcurl && sudo make clean
		cd ../twitterClient

