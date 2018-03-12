<p>- curl -fsSL https://get.docker.com/ | sh </p>

<p>- Show info docker <br />
   -  docker inspect {container_id/name}</p>

<p>- Create volumes <br />
   - docker volume create mysql_cnf<br />
   - cd /var/lib/docker/volumes<br />
   - docker volume rm mysql_cnf<br />
   - docker volume create mysql_wiki <br />

<p>- Pull một image từ Docker Hub<br />
  docker pull {image_name}</p>
<p>- Liệt kê các images hiện có<br />
  docker images</p>
<p>- Xóa một image<br />
  docker rmi {image_id/name}</p>
<p>- Liệt kê các container đang chạy<br />
  docker ps<br />
  docker ps -a - Liệt kê các container đã tắt</p>
<p>- Xóa một container<br />
  docker rm -f {container_id/name}</p>
<p>- Đổi tên một container<br />
  docker rename {old_container_name} {new_container_name}</p>
<p>- Khởi động một container <br />
  docker start {new_container_name}<br />
  docker exec -it {new_container_name} /bin/bash</p>
<p>- Tạo mới một container, đồng thời khởi động với tùy chọn cổng và volume<br />
  docker run --name {container_name} -p {host_port}:{container_port} -v {/host_path}:{/container_path} -it {image_name} /bin/bash<br />
  docker run -it -d --name mysql02 -v /data/mysql/mysql02/data:/var/lib/mysql -v msyql_cnf:/etc/mysql/ -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 mysql:5.6.38
</p>
  
<p>- Xem các thay đổi trên container<br />
  docker diff {container_name}</p>
<p>- Commit các thay đổi trên container và image<br />
  docker commit -m &quot;message&quot; {container_name} {image_name}</p>
<p>- Save image thành file .tar<br />
  docker save {image_name} &gt; {/host_path/new_image.tar}</p>
<p>- Load image thành file .tar<br />
  docker load  docker load < {/host_path/new_image.tar}</p>
<p>- Export image thành file .tar<br />
  docker export {image_name} &gt; {/host_path/new_image.tar}</p>
<p>- Import image thành file .tar<br />
  cat {/host_path/new_image.tar} | docker import - {image_name}</p>   
<p>- Tạo một image mới từ file .tar<br />
cat musashi.tar | docker import - {new_image_name}:latest</p>
<p>- Xem lịch sử các commit trên image<br />
docker history {image_name}</p>
<p>- Khôi phục lại images từ IMAGE_ID<br />
  docker tag {iamge_id} {image_new_name}:{tag}</p>
<p>- Build một image từ container<br />
  docker build -t {container_name} .<br />
  - Dấu . ở đây ám chỉ Dockerfile đang nằm trong thư mục hiện tại.</p>
<p>- Em có một câu hỏi về docker, mỗi khi chạy lệnh docker run với image X, docker đều tạo ra một container mới với PID mới (có thể dùng lệnh docker ps sẽ thấy), tuy nhiên mình có cách nào để docker run một image X với một container đã tồn tại không ?<br />
  - Em thấy nếu cứ mỗi lần develop mà chạy docker run thì sau này sẽ càng nhiều container id được tạo ra, cái này có thể gây lãng phí tài nguyên hệ thống nhỉ :joy:<br />
  - Em có thử qua lệnh docker exec tuy nhiên nó lại không có option bind port và volume như lệnh docker run<br />
  - do bản chất của docker là immutable nên em không thể run với một container đã tồn tại được đâu. Em có thể consider về việc tự động clean đi các container cũ, ví dụ với một command kiểu như<br />
  $ docker ps -a | grep 'weeks ago' | awk '{print $1}' | xargs --no-run-if-empty docker rm<br />
</p>
