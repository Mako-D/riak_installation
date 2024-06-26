# What is this repo about?
While reading the book "Seven Databases in Seven Weeks" 1st ed., I encountered difficulties in installing Riak (3th chapter). When trying to build a repository, many dependencies were not automatically installed. So that I wouldn't forget what to do and how to do it, I decided to leave a brief Riak installation manual somewhere. The instruction is relevant for the "develop" branch.
# Instruction
## 1. Prep Linux
Doing the routine steps when installing a new Linux installation
```shell
sudo apt-get update
sudo apt-get upgrade
```
# 2. Install dependent packages
Since we will be installing Riak from the Git repository, we will need to install Git
```shell
sudo apt-get install git
```
Also we need make,
```shell
sudo apt-get install make
```
And of course, since riak is written in erlang, we'll need erlang as well
```shell
sudo apt-get install erlang
```
And others...
```shell
sudo apt-get install g++
sudo apt-get install cmake
sudo apt-get install libsnappy-dev
sudo apt-get install libpam0g-dev
```
# 3. Install Riak
Clone Riak repo.
```shell
git clone https://github.com/basho/riak.git
```
Choose branch, I use 'develop' (because riak-3.2.0, doesn't work, idk why, and riak-3.0.9 doesn't work with erlang 24). In my case, the commit that was relevant in the “develop” branch worked.
```
b8eb83a1348db9ebb3a85963689cf9b3f9594ac4
```
And build project with "devrel" to make multiple databases for experimentals.
```shell
make devclean
make devrel
```
In new versions of Riak, 8 databases are created instead of 3.
# 4. Riak setup

After assembly, most often the ports do not intersect.
If you want to interact with the database from the local network (I run Riak in an LXS container on Proxmox, but I want to interact with them through another computer), change in file
```shell
cd ~/riak/dev/dev1/riak/etc
nano riak.conf
```
the line
```
listener.http.internal = 0.0.0.0:[PORT]
listener.protobuf.internal = 0.0.0.0:[PORT]
```

# FAQ
Sometimes I can't fetch repo with make all, for example 'leveled'
```shell
cd ~
git clone https://github.com/martinsumner/leveled
cd leveled
git checkout a033e280e67931582cc9625993268db126abb4ff
cp -R ~/leveled/ ~/riak/_build/default/lib
```
Where I checkouted to version which ref in fetch
```shell
Fetching leveled (from {git,"https://github.com/martinsumner/leveled",
                   {ref,"a033e280e67931582cc9625993268db126abb4ff"}})
```
