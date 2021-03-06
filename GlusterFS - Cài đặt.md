# GlusterFS

<a name="Caidat"></a>
### 4.2 Cài đặt và cấu hình trên các Server

Đầu tiên, tạo một thư mục trên 2 GlusterFS server nằm trên phân vùng khác với phân vùng / 

Ở đây, ta add thêm 1 ổ cứng mới ở cả 2 server và phân vùng, format thành định dạng xfs, mount vào /mnt 

Đầu tiên, tạo partition:

`# fdisk /dev/vdb`

Format the partition:

`# mkfs.xfs /dev/vdb1`

Mount partition vào thư mục /mnt và tạo thư mục /mnt/brick1

`# mount /dev/vdb1 /mnt && mkdir -p /mnt/brick1`

Khai báo vào file cấu hình /etc/fstab để khi restart server, hệ thống sẽ tự động mount vào thư mục.

`# echo "/dev/vdb1 /mnt xfs defaults 0 0"  >> /etc/fstab`

**Cài đặt GlusterFS:**

`# yum install centos-release-gluster -y`

`# yum install epel-release -y`

`# yum install glusterfs-server`

`# systemctl start glusterd`

`# systemctl enable glusterd`

**Add 1 node có địa chỉ là 10.145.37.92 vào pool (đang ở trên server 10.145.37.90)**:

```
# gluster peer probe 10.145.37.92
peer probe: success
```

Trên node 10.145.37.90 cũng làm tương tự

Xem status của pool

```
# gluster peer status 
Number of Peers: 1
Hostname: 10.145.37.92
Port: 24007
Uuid: 40221832-c1a4-4a5b-ae12-8e8ddc1682d3
State: Peer in Cluster (Connected)
```

#### Taọ Volume Distributed

Tạo Volume "testvol" từ 1 node 10.145.37.90

`# gluster volume create testvol transport tcp 10.145.37.90:/mnt/brick1`

#### Tạo Volume Replicated

Tạo Volume "testvol2" từ 2 node 10.145.37.90 và 10.145.37.92 (chỉ cần tạo trên 1 trong 2 server):

`# gluster volume create testvol2 rep 2 transport tcp 10.145.37.90:/mnt/brick1 10.145.37.92:/mnt/brick1`

Đây là loại volume Replicated volume: dữ liệu sẽ được nhân bản đến những brick còn lại. Khi dữ liệu trên 1 brick bị mất (tức là dữ liệu lưu trên 1 con server) thì dữ liệu vẫn còn trên brick còn lại và tự động đồng bộ lại cho cả 2 server. Đảm bảo dữ liệu luôn đồng bộ và sẵn sàng.

Thông số rep là số lượng brick.

#### Tạo Volume Stripe

Tạo Volume "testvol3" từ 2 node 10.145.37.90 và 10.145.37.92 (chỉ cần tạo trên 1 trong 2 server):

`# gluster volume create testvol3 stripe 2 transport tcp 10.145.37.90:/mnt/brick1 10.145.37.92:/mnt/brick1`

*Note: thông số stripe là số lượng brick.*

#### Tạo Volume Distributed Replicated 

Tạo Volume Distributed Replicated từ 4 node 10.145.37.90, 10.145.37.92, 10.145.37.100, và 10.145.37.102

Đầu tiên add các node vào pool:

```
# gluster peer probe 10.145.37.92
# gluster peer probe 10.145.37.100
# gluster peer probe 10.145.37.102
```

Tạo Volume "testvol4" từ các node trên:

`# gluster volume create testvol4 replica 2 transport tcp 10.145.37.90:/mnt/brick1 10.145.37.92:/mnt/brick1 10.145.37.100:/mnt/brick1 10.145.37.102:/mnt/brick1`

*Note: Lưu ý số lượng brick là một bội số của số lượng replicated.*

#### Tạo Volume Stripe Replicated 

Tạo Volume Stripe Replicated từ 4 node có địa chỉ 10.145.37.90, 10.145.37.92, 10.145.37.100 và 10.145.37.102

Đầu tiên add các node vào pool:

```
# gluster peer probe 10.145.37.92
# gluster peer probe 10.145.37.100
# gluster peer probe 10.145.37.102
```

Tạo Volume "testvol5" từ các node trên:

`# gluster volume create testvol5 stripe 2 replica 2 transport tcp 10.145.37.90:/mnt/brick1 10.145.37.92:/mnt/brick1 10.145.37.100:/mnt/brick1 10.145.37.102:/mnt/brick1`

*Note: Lưu ý số lượng brick là một bội số của số lượng stripe*

**Start Volume:**

Sau khi tạo Volume, bạn cần phải start volume đó lên

`# gluster volume start testvol`

Bạn có thể kiểm tra lại bằng cách xem thông tin volume:	

```
# gluster volume info
Volume Name: testvol
Type: Distribute
Volume ID: 5d791191-f98c-4c24-ab23-11a0a796f714
Status: Started
Number of Bricks: 2
Transport-type: tcp
Bricks:
Brick1: 10.145.37.90:/mnt/brick1
Brick2: 10.145.37.92:/mnt/brick1
```
<a name="CaidatCl"></a>
### 4.4 Cài đặt trên Client

`# apt-get install glusterfs-client`

Mount và sử dụng:

`# mount -t glusterfs 10.145.37.90:/testvol /mnt`

**Chú ý:** 

*Sau khi 1 brick đã được dùng để tạo 1 volume, mà brick đó đã được remove ra khỏi volume hoặc volume đó đã bị xóa thì brick đó không tạo được volume khác. Vì thế để có thể tận dụng lại những brick đó để tạo 1 volume khác, trước khi tạo volume ta phải làm như sau:*

```
# setfattr -x trusted.glusterfs.volume-id /mnt/brick1/
# setfattr -x trusted.gfid /mnt/brick1/
# rm -rf /mnt/brick1/.glusterfs
```

<a name="Motsocaulenh"></a>
### 4.3 Một số câu lệnh khác khi sử dụng GlusterFS

Add 1 node vào pool:

`# gluster peer probe <server>`

Trong đó `<server>` là địa chỉ của server mà mình muốn add vào

Xem status của pool:

`# gluster peer status`

Xóa node ra khỏi pool:

`# gluster peer detach <server>`

Trong đó `<server>` là địa chỉ của server mà mình muốn xóa

Tạo volume:

`# gluster volume create <volume-name> [stripe COUNT | replica COUNT] [transport [tcp |rdma] ] <brick1> <brick2>.... <brick n>`

Start volume:

`# gluster volume start <volume-name>`

Trong đó `<volume-name>` là tên volume cần start

Xem thông tin volume đã tạo:

`# gluster volume info`

Stop volume:

`# gluster volume stop <volume-name>` 

Trong đó `<volume-name>` là tên volume cần stop

Xóa volume:

`# gluster volume delete <volume-name>` 

Add thêm brick vào volume:

`# gluster volume add-brick <volume-name> <server:/data>`

Trong đó `<server:/data>` là đường dẫn của brick cần add, ví dụ trong bài lab trên là đường dẫn `10.145.37.92:/mnt/brick1`

Tương tự Remove brick ra khỏi volume:

`# gluster volume remove-brick <volume-name> <server:/data>` 

Migrate volume: chuyển dữ liệu từ 1 brick trong Pool đến đến brick khác nằm ngoài Pool:

```
# gluster volume replace-brick <volume-name> <server1:/data1> <server2:/data2> start // bắt đầu chuyển dữ liệu từ brick data1 đến data2
# gluster volume replace-brick <volume-name> <server1:/data1> <server2:/data2> status // xem quá trình chuyển dữ liệu
# gluster volume replace-brick <volume-name> <server1:/data1> <server2:/data2> commit
```

Rebalance Volume: đồng bộ dữ liệu khi thêm, xóa brick:

```
# gluster volume rebalance <volume-name> fix-layout start 
# gluster volume rebalance <volume-name> migrate-data start 
# gluster volume rebalance <volume-name> start
```

<a name="Tailieu"></a>
## Tài liệu tham khảo 

http://congdonglinux.vn/forum/showthread.php?1282-C%C3%A0i-%C4%91%E1%BA%B7t-Store-Server-s%E1%BB%AD-d%E1%BB%A5ng-GlusterFS

http://www.gluster.org/documentation/quickstart/

http://www.slideshare.net/openstackindia/glusterfs-and-openstack?related=3

http://www.slideshare.net/keithseahus/glusterfs-as-an-object-storage?related=1

http://www.server-world.info/en/note?os=CentOS_6&p=openstack_icehouse2&f=2

http://www.gluster.org/community/documentation/index.php/GlusterFS_Glance

http://docs.openstack.org/admin-guide-cloud/content/glusterfs_backend.html


