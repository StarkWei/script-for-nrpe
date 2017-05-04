# script for nrpe

```sh
  check_diskIO：監控Linux主機，HDD diskI/O使用率多寡，單位是%，範例如下：
    check_diskIO -d / -w 50 -c 60
```
```sh
  check_diskInodes：監控Linux主機，HDD disk inodes使用率多寡，單位是%，範例如下：
    diskInodes -d / -w 50 -c 60
```
```sh
  check_diskInodes：監控Linux主機，HDD disk inodes使用率多寡，單位是%，範例如下：
    diskInodes -d / -w 50 -c 60
```
```sh
  check_networkstat：監控Linux主機上網路狀態數量多寡，範例如下：
    check_networkstat -s CLOSE_WAIT -w 500 -c 550
```
```sh
  check_session：監控Linux主機上service的seesion數，範例如下：
    check_session -s nginx -p 80 -w 500 -c 550
```
