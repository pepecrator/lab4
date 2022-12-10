root@fedorpc:/home/fedor/labs/lab4# uname -r
5.15.0-56-generic
root@fedorpc:/home/fedor/labs/lab4# make clean
make -C /lib/modules/5.15.0-56-generic/build M=/home/fedor/labs/lab4 clean
make[1]: вход в каталог «/usr/src/linux-headers-5.15.0-56-generic»
  CLEAN   /home/fedor/labs/lab4/Module.symvers
make[1]: выход из каталога «/usr/src/linux-headers-5.15.0-56-generic»
root@fedorpc:/home/fedor/labs/lab4# make -C /lib/modules/5.15.0-56-generic/build M=/home/fedor/labs/lab4 modules
make: вход в каталог «/usr/src/linux-headers-5.15.0-56-generic»
  CC [M]  /home/fedor/labs/lab4/lab4.o
  MODPOST /home/fedor/labs/lab4/Module.symvers
  CC [M]  /home/fedor/labs/lab4/lab4.mod.o
  LD [M]  /home/fedor/labs/lab4/lab4.ko
  BTF [M] /home/fedor/labs/lab4/lab4.ko
Skipping BTF generation for /home/fedor/labs/lab4/lab4.ko due to unavailability of vmlinux
make: выход из каталога «/usr/src/linux-headers-5.15.0-56-generic»
root@fedorpc:/home/fedor/labs/lab4# insmod lab4.ko
root@fedorpc:/home/fedor/labs/lab4# dmesg | tail -n 1
[ 1171.677582] Entering: hello_init
root@fedorpc:/home/fedor/labs/lab4# gcc lab4_1.c -o gg
lab4_1.c: In function ‘main’:
lab4_1.c:28:23: warning: implicit declaration of function ‘getpid’ [-Wimplicit-function-declaration]
   28 |     src_addr.nl_pid = getpid(); /* self pid */
      |                       ^~~~~~
lab4_1.c:59:40: warning: format ‘%s’ expects argument of type ‘char *’, but argument 2 has type ‘void *’ [-Wformat=]
   59 |     printf("Received message payload: %s\n", NLMSG_DATA(nlh));
      |                                       ~^
      |                                        |
      |                                        char *
      |                                       %p
lab4_1.c:60:5: warning: implicit declaration of function ‘close’; did you mean ‘pclose’? [-Wimplicit-function-declaration]
   60 |     close(sock_fd);
      |     ^~~~~
      |     pclose
root@fedorpc:/home/fedor/labs/lab4# ./lab4_1
bash: ./lab4_1: Нет такого файла или каталога
root@fedorpc:/home/fedor/labs/lab4# ./gg
Sending message to kernel
Waiting for message from kernel
Received message payload: Hello from kernel

