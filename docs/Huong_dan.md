### Hướng dẫn sử dụng scripts

### Mô hình 

<img src="/img/1.jpg">

### 1.Các bước thực hiện

**1.1. Đặt IP theo IP Planning cho từng node.**

* Trên Controller thực hiện

``` sh
curl -O https://raw.githubusercontent.com/anhbka/Opentack-scripts-Queens-NoHA/master/scripts/setup_ip.sh
bash setup_ip.sh controller 192.168.239.180 10.10.10.180 172.16.10.180
```


* Trên Compute1 thực hiện

``` sh
curl -O https://raw.githubusercontent.com/anhbka/Opentack-scripts-Queens-NoHA/master/scripts/setup_ip.sh
bash setup_ip.sh compute1 10.10.10.181 172.16.10.181 192.168.239.181
```
* Trên Compute2 thực hiện

``` sh
curl -O https://raw.githubusercontent.com/anhbka/Opentack-scripts-Queens-NoHA/master/scripts/setup_ip.sh
bash setup_ip.sh compute2 10.10.10.182 172.16.10.182 192.168.239.182
```

* Thực hiện trên máy Cinder

``` sh
curl -O https://raw.githubusercontent.com/anhbka/Opentack-scripts-Queens-NoHA/master/scripts/setup_ip.sh
bash setup_ip.sh cinder 10.10.10.183 172.16.10.183 192.168.239.183
```

### Thực hiện script cài đặt OpenStack

### 2. Thực hiện cài đặt trên Controller

2.1. Tải script

Đứng trên node CTL1 và thực hiện các bước dưới.

Chuyển sang quyền root: 
`su -`

* Cài đặt git và script cài đặt.

``` sh
yum -y install git
git clone https://github.com/anhbka/Opentack-scripts-Queens-NoHA.git
mv Opentack-scripts-Queens-NoHA/scripts/ /root
cd scripts
chmod +x *.sh
```
Nếu muốn sửa các IP thì sử dụng VI hoặc VIM để sửa, cần lưu ý tên NICs và địa chỉ IP cần phải tương ứng (trong này này tên NICs là ens33, ens34, ens35)

Nếu cần thiết thì cài ứng dụng `byobu` để khi các phiên `ssh` bị mất kết nối thì có thể sử dụng lại (để sử đụng lại thì cần ssh vào và gõ lại lệnh byobu)

``` sh
sudo yum -y install epel-release
sudo yum -y install byobu
```
* Gõ lệnh byobu

`byobu`

2.2. Thực thi script noha_ctl_prepare.sh

* Thực thi script noha_ctl_prepare.sh

`bash node_prepare.sh`

* Trong quá trình chạy script, cần nhập password cho tài khoản root của máy COM1 và COM2

2.3. Thực thi script noha_ctl_install_db_rabbitmq.sh để cài đặt DB và các gói bổ trợ.

`bash ctl_install_db_rabbitmq.sh`























