# What is this repo about?
While reading the book "Seven Databases in Seven Weeks" 1st ed., I encountered difficulties in installing Riak (3th chapter). When trying to build a repository, many dependencies were not automatically installed. So that I wouldn't forget what to do and how to do it, I decided to leave a brief Riak installation manual somewhere. The instruction is relevant for the "develop-3.2" branch.
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
Clone from Riak repo and checkout to branch 'develop-3.2'
```shell
git clone https://github.com/basho/riak.git
```
Choose branch, for example 'riak-3.2.0',
```shell
git checkout riak-3.2.0
```
And start install
```shell
make rel
```
# FAQ
Sometimes I can't fetch repo with make all, for example 'leveled'
```shell
cd ~
git clone https://github.com/martinsumner/leveled
cd leveled
git checkout a033e280e67931582cc9625993268db126abb4ff
cp -R cp -R ~/leveled/ ~/riak/_build/default/lib
```
Where I checkouted to version which ref in fetch
```shell
Fetching leveled (from {git,"https://github.com/martinsumner/leveled",
                   {ref,"a033e280e67931582cc9625993268db126abb4ff"}})
```
