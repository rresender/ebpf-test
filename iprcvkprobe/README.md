mount | grep debugfs

debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)

bpftool btf dump file /sys/kernel/btf/vmlinux format c > vmlinux.h

clang -Wall -Werror -fno-stack-protector -g -O2 -target bpf -emit-llvm -D__TARGET_ARCH_x86 -I/usr/include/x86_64-linux-gnu -I../libbpf/src -c iprcv.bpf.c -o iprcv.bpf.ll

llc -march=bpf -filetype=obj -o ip rcv.bpf.o iprcv.bpf.ll

gcc iprcv.c -L/home/ubuntu/libbpf/src -lbpf -lelf -lz -I/home/ubuntu/libbpf/src -o iprcv

#Terminal 1
sudo ./iprcv &

sudo bpftool prog list

#Termial 2
curl www.example.com
