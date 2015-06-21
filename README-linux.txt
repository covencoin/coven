apt-get update -y
apt-get install sudo unzip nano git make automake build-essential libboost-all-dev libssl-dev libdb++-dev -y

sudo dd if=/dev/zero of=/swap bs=50M count=16
chmod 0600 /swap
sudo mkswap /swap
sudo swapon /swap

git clone https://github.com/covencoin/coven

cd coven/src

make -f makefile.unix USE_UPNP=-

mkdir ~/.Coven
nano  ~/.Coven/Coven.conf
   rpcuser=*********
   rpcpassword=************************************
   

./Covend -seednode=ONE.OF.THE.ADDNODES &
./Covend getinfo
./Covend getpeerinfo

# if it does not fully sync right away, kill and restart
./Covend stop
killall Covend
./Covend -seednode=ONE.OF.THE.ADDNODES &


# more info:
./Coven &
./Coven --help
./Coven help

