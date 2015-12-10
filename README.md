# apache2tune
Automatic Calculate the Variables for Mod_Prefork in Apache2 - Works with Centos or Debian Base (Ubuntu, Mint, etc)


Working the MaxClients value for mod_prefork

This bash script calculate using your server resources the calculations for configure mode_prefork finding  the average size of an Apache2 thread then restarts Apache2 so that the correct "free size" value can be obtained. 

It then divides the remainder by the Apache2 process size. The value you get should be roughly the right value for your MaxClients. 

It will also show you how much disk swapped or virtual memory you are using as well as the size of your MySQL process.

Therefore if your virtual memory is greater than the size of your total RAM e.g if you are using 1.5GB of hard disk space as virtual memory and only have 1GB of RAM then it will show an error message.

Also as a number of Apache tuners claim that your MinSpareServers should be 10-25% of your MaxClients value and your MaxSpareServers value 25-50% of your MaxClientsValue I have also included the calculations for these settings as well. 

I recommend to before execute this script install Mod Ruid2 will improve the performance of your server
 
apt-get install libapache2-mod-ruid2

service apache2 restart

INSTALL APACHE2TUNE
git clone https://github.com/royalterra/apache2tune.git

cd apache2tune

chmod +x Apache2tune.sh

./Apache2tune.sh

And you will get something like that test in my home computer with 8 gb ram 

Calculate MaxClients by dividing biggest Apache thread by free memory

Stopping apache2 to calculate the amount of free memory

Starting apache2 again

Total memory 8192

Free memory 6147

Amount of virtual memory being used 0

Largest Apache Thread size 44

Amount of memory taking up by MySQL 471

Virtual memory is ok

Total Free Memory 6147

MaxClients should be around 139

MinSpareServers should be around 34

MaxSpareServers should be around 69

Of course this script will calculate accordig to your server performance .  With a veriables like that I setup 
MaxRequestsPerChild 1500

All depends of yoru Server CPU Ram and performance but now you can get a numbers for play around 



