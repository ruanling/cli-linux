# certbot
1. wget https://dl.eff.org/certbot-auto	
2. chmod a+x ./certbot-auto	
3. ./certbot-auto certonly --standalone --email EMAIL_ADDRESS_HERE -d DOMAIN_HERE	
4. /home/certbot-auto certonly --webroot -w /home/ebuda.vn/ -d ebuda.vn	
5. certbot renew --pre-hook "service nginx stop" --post-hook "service nginx start"

#FTP server với virtual user
1. yum install db4-utils db4 -y
2. Copy virtual_users.txt vào thư mục /etc/vsftpd/virtual_users.txt
3. db_load -T -t hash -f /etc/vsftpd/virtual_users.txt /etc/vsftpd/virtual_users.db
4. Copy vsftpd_virtual vào thư mục /etc/pam.d/vsftpd_virtual
5. Copy folder vsftpd_user_conf vào /etc/vsftpd
6. Sửa file user theo thư mục tương ứng

#CHMOD
0. chown -R root:root /home/test
1. chmod 775 testfile
2. chmod 400 testfolder
3. chmod u+s testfolder (cho phép mọi thành viên không thuộc người sở hữu và không thuộc group sở hữu có thể execute folder)
#Một vài ví dụ thêm về kiểu ugo:
1.o+rws: cho phép user sở hữu có full quyền
2.g+rw: cho phép group sở hữu có quyền đọc và ghi
3.u+w: cho phép các user còn lại có quyền đọc
4.a+rws: cho phép toàn bộ user có full quyền (777)


