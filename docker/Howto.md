## Docker setup
1. Ubuntu
    
```bash
sudo apt-get install docker
sudo docker pull centos:7.0.1406
sudo docker run -it --name ceph-dev centos:7.0.1406 bash
#Running the following commands inside the ceph-dev container
cd ~
git clone https://github.com/anglenet/ceph
cd ceph && git submodule update --init --recursive && git remote add ceph git://github.com/ceph/ceph 
./install-deps.sh
./do_cmake.sh && cd build && make
```
