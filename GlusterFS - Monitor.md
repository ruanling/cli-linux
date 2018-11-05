# Monitor Gluster:

```
- Viewing Peer Status
# gluster peer status

- Listing Servers
# gluster pool list

- Displaying Volume Information
# gluster volume info test_volume

volume status [all | <VOLNAME> [nfs|shd|<BRICK>|quotad|tierd]] [detail|clients|mem|inode|fd|callpool|tasks|client-list]

```

Start Profiling
You must start the Profiling to view the File Operation information for each brick.

```
# gluster volume profile test_volume start
# gluster volume profile test_volume stop

- You can view the I/O information of each brick by using the following command
# gluster volume profile test_volume info

```

Running GlusterFS Volume TOP
- Lệnh GlusterFS Volume Top cho phép bạn xem các số liệu hiệu suất của các khối glusterfs như đọc, ghi, mở các cuộc gọi, các cuộc gọi đọc tập tin, các cuộc gọi ghi tập tin, các cuộc gọi mở thư mục và các cuộc gọi thực. Lệnh trên cùng hiển thị tối đa 100 kết quả.

```
# gluster volume top test_volume open

- volume top <VOLNAME> {open|read|write|opendir|readdir|clear} [nfs|brick <brick>] [list-cnt <value>] 
VD: # gluster volume top data open brick HA02:/gluster/data list-cnt 10

- volume top <VOLNAME> {read-perf|write-perf} [bs <size> count <count>] [brick <brick>] [list-cnt <value>

- để xem hiệu suất đọc trên máy chủ gạch: / xuất / khối lượng kiểm tra, kích thước khối 256 của số 1 và danh sách 10:
# gluster volume top data read-perf bs 256 count 1 brick HA01:/gluster/data list-cnt 10

- để xem hiệu suất ghi trên máy chủ gạch: / xuất / khối lượng kiểm tra, kích thước khối 256 của số 1 và danh sách 10:
# gluster volume top data write-perf bs 128 count 1 brick HA01:/gluster/data list-cnt 10

```
Chech thông tin Replicate

```
# gluster volume heal volume info
```
