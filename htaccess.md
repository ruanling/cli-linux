
<p><strong>1.1. .htaccess là gì</strong></p>
<p>.htaccess là một file cấu hình sử dụng cho các web server chạy Apache. .htaccess dùng để thiết lập các tùy chọn: thực thi hay loại bỏ các chức năng, tính năng của Apache<br />
</p>
<p><strong>1.2. Ý nghĩa ký hiệu định nghĩa trong .htaccess</strong></p>
<p>- : cho phép server bỏ qua dòng này<br />
  [F] : Forbidden, hướng dẫn server trả về lỗi 403 cho client<br />
  [L] : Last rule, hướng dẫn server ngừng ghi lại sau khi một chỉ thị đã được xử lý<br />
  [N] : Next, chỉ dẫn cho Apache trả về luật rewrite cho tới khi tất cả các chỉ thị rewrite được hoàn tất.<br />
  [G]: Gone, chỉ dẫn server chuyển thông điệp Gone<br />
  [P]: Proxy, chỉ dẫn server sử dụng các request cung cấp bởi mod_proxy<br />
  [C]: Chain, chỉ dẫn server gắn luật trước với luật sau nó<br />
  [R]: Redirect, hướng dẫn Apache đưa ra một chuyển hướng<br />
  [NC]: No case, xác định bất cứ trường hợp nào liên quan tới nó là vô lý (Không thể xảy ra)<br />
  [PT]: Pas Through: chỉ dẫn mod_rewrite để vượt qua cơ chế ghi lại URL cho các xử lý xa hơn<br />
  [OR]: Or, là cú pháp logic bình thường (biểu thức kết hợp đúng khi một trong hai biểu thức con của nó đúng)<br />
  [NE]: No Escape: hướng dẫn server lọc đầu ra<br />
  [NS]: No Subresquest: hướng dẫn server giữ chỉ thị nếu là một request con từ bên trong<br />
  [QSA]: gắn thêm chuỗi truy vấn vào cuối URL<br />
  [S=x]: Skip: chỉ dẫn server dừng lại x luật<br />
  [E=variable:value]: Environment Variale: chỉ dẫn server thiết lập giá trị tài nguyên<br />
  [T=MIME-type]: Mime Type: mô tả loại mime của tài nguyên đích<br />
  []: xác định một tập các ký tự trong đó bất cứ ký tự nào có trong ngoặc xuất hiện sẽ được match<br />
  []+: tập các ký tự trong đó bất cứ kết hợp nào với nó cũng được match<br />
  [a-z] : match với tất cả các ký tự từ a-z, theo bảng chữ cái. Có thể có thêm: [a-zA-Z]<br />
  a{n}: xác định số ký tự sẽ mở rộng cùng với ký tự đầu, tức là khi match được ký tự đầu sẽ lấy thêm bao nhiêu ký tự tiếp theo. Ví dụ: x{3} sẽ lấy: x’s, xad, …<br />
  a{n,} : như a{n} nhưng có thể lấy 3 hoặc nhiều hơn<br />
  a{n,m}: như a{n} nhưng sẽ lấy trong khoảng từ n tới m<br />
  (): nhóm các ký tự lại với nhau, xem chúng như 1 đơn vị đơn lẻ<br />
  ^: ghi chú bắt đầu chuỗi regex<br />
  $: ghi chú kết thúc chuỗi regex<br />
  ? : cho phép chọn lựa ký tự.Ví dụ: monzas? sẽ match với monza hoặcmonzas<br />
  ! : mô tả một phủ định, sẽ match với tất cả thứ gì khác với các ký tự sau !<br />
  . : thể hiện cho bất cứ ký tự đơn nào<br />
  +: match với một hoặc nhiều ký tự<br />
  *: match với 0 hoặc nhiều ký tự<br />
  |: phép hoặc logic<br />
  \: thêm vào trước các ký tự đặc biệt để có thể sử dụng chúng như các ký tự bình thường<br />
  .* : không có ký tự nào hoặc nhiều ký tự bất kỳ<br />
  ^$: định nghĩa một chuỗi rỗng<br />
  ^.*$: sử dụng để match mọi thứ<br />
  [^/.]: định nghĩa 1 ký tự là “/” hoặc “.”<br />
  [^/.]+: định nghĩa bất cứ số lượng ký tự nào chứa “/” hoặc “.”<br />
  http://: là một chuỗi bình thường<br />
  ^domain.*: định nghĩa một chuỗi bắt đầu với “domain”<br />
  ^domain\.com$: xác định sự mở rộng của chuỗi “domain.com”<br />
  -d: kiểm tra nếu chuỗi là một directory<br />
  -f: kiểm tra nếu một chuỗi là một file<br />
  -s: kiểm tra nếu file trong chuỗi kiểm tra có 1 giá trị khác 0</p>
<p><strong>1.3. Mã redirect</strong></p>
<p>301 – Move permanently<br />
  302 – Move temporarily<br />
  403 – Forbidden<br />
  404 – Not found<br />
  410 – Gone</p>
<p><strong>1.4. Cách sử dụng .htaccess</strong></p>
<p>Tạo file .htaccess (chú ý đây là tên đầy đủ, không phải là phần mở rộng), tiến hành các thiết lập cấu hình trong file và đặt ở trong thư mục mong muốn thực hiện các cấu hình đó.</p>
<p>Ví dụ:<br />
  AuthName &quot;Member's Area Name&quot;<br />
  AuthUserFile /path/to/password/file/.htpasswd<br />
  AuthType Basic<br />
  require valid-user<br />
  ErrorDocument 401 /error_pages/401.html<br />
  AddHandler server-parsed .html</p>
<p>Ví dụ trên cấu hình sử dụng password bảo vệ thư mục và chuyển hướng tới trang 401.html khi gặp lỗi 401.</p>
<p>Chú ý:</p>
<p>- Upload file .htaccess ở chế độ ASCII thay vì chế độ BINARY hay các chế độ khác do cơ chế chuyển dữ liệu ở các chế độ là khác nhau.<br />
  - Việc cấp quyền truy cập, sử dụng và thực thi file .htaccess có thể gây ra lỗi, cài đặt quyền 755 hoặc quyền thực thi với file<br />
  - Comment lại các thông tin cấu hình quan trọng để dễ dàng cho người tiếp quản sau này hoặc cho chính bản than khi phải cấu hình lại hoặc khắc phục sự cố nào đó</p>
<p><strong>2. Những cấu hình cần thiết</strong></p>
<p><strong>2.1. Enable basic rewriting</strong></p>
<p>Server có thể không bật chế độ “mod_rewite” mặc định, để đảm bảo chế độ này được bật, thêm vào file .htaccess tại thư mục root:<br />
  - enable basic rewriting<br />
  RewriteEngine on</p>
<p><strong>2.2. Enable Symbolic links</strong></p>
<p>Xem về Symbolic links tại: http://en.wikipedia.org/wiki/Symbolic_link. Để chế độ này hoặc động, tính năng: AllowOverride Options cần được enable.<br />
  - enable symbolic links<br />
  Options +FollowSymLinks</p>
<p><strong>2.3. Enable AllowOverride</strong></p>
<p>Đối với các chỉ thị cần tính năng AllowOverride để thực thi như: FollowSymlinks, … Khi cần enable tính năng này tại một thư mục nào đó, ta thêm vào .htaccess (Có thể cấu hình tại file server để áp dụng toàn bộ):</p>
<p>- enable allowoverride privileges<br />
  &lt;Directory /www/replace/this/with/actual/directory&gt;<br />
  AllowOverride Options<br />
  &lt;/Directory&gt;</p>
<p><strong>2.4. Đặt tên lại file .htaccess</strong></p>
<p>Không phải mọi hệ thống đều thích định dạng .htaccess, có thể thay đổi tên này (thực hiện trên file cấu hình của server):<br />
  - rename htaccess files<br />
  AccessFileName ht.access</p>
<p>Khi thay đổi tên file .htaccess, cần cập nhật tất cả các cấu hình liên quan. Ví dụ: nếu bạn bảo vệ .htaccess với FilesMatch, định dạng lại file này (với .htaccess đã đổi thành: ht.access):<br />
  - protect renamed htaccess files<br />
  &lt;FilesMatch &quot;^ht\.&quot;&gt;<br />
  Order deny,allow<br />
  Deny from all<br />
  &lt;/FilesMatch&gt;</p>
<p><strong>2.5. Giữ lại các luật đã được định nghĩa trong httpd.conf</strong></p>
<p>Tiết kiệm thời gian và nỗ lực định nghĩa lại các luật lặp lại cho nhiều host ảo với chỉ 1 file httpd.conf, để đơn giản hơn ta cấu hình .htaccess kế thừa tập luật từ httpd.conf<br />
  RewriteOptions Inherit</p>
<p><strong>3. Hiệu năng</strong><br />
<strong>3.1. Tăng hiệu năng thông qua AllowOverride</strong></p>
<p>Việc cấu hình AllowOverride ở thư mục gốc, server sẽ phải tìm kiếm ở tất cả các thư mục để xem nơi nào .htaccess tồn tại, điều này làm chậm tốc độ xử lý. Để hạn chế điều này, disable chế độ AllowOverride tại thư mục gốc và bật lên ở những nơi cần dùng, để disable:<br />
  - increase performance by disabling allowoverride<br />
  AllowOverride None</p>
<p><strong>3.2. Tăng hiệu năng bằng cách truyền tập các ký tự</strong><br />
  - pass the default character set<br />
AddDefaultCharset utf-8</p>
<p><strong>3.3. Tăng hiệu năng bởi việc bảo vệ bandwidth</strong><br />
  - preserve bandwidth for PHP enabled servers<br />
  &lt;ifmodule mod_php4.c&gt;<br />
  php_value zlib.output_compression 16386<br />
&lt;/ifmodule&gt;</p>
<p><strong>3.4. Disable chữ ký server</strong><br />
  - disable the server signature<br />
ServerSignature Off</p>
<p><strong>3.5. Cài đặt server timezone</strong><br />
  - set the server timezone<br />
SetEnv TZ America/Washington</p>
<p><strong>3.6. Đặt địa chỉ email cho quản trị server</strong><br />
</p>
<p>- set the server administrator email<br />
  SetEnv SERVER_ADMIN default@domain.com</p>
<p><strong>3.7. Tăng tốc độ duyệt site bằng việc enable file caching</strong></p>
<p>- cache images and flash content for one month<br />
  &lt;FilesMatch &quot;.(flv|gif|jpg|jpeg|png|ico|swf)$&quot;&gt;<br />
  Header set Cache-Control &quot;max-age=2592000&quot;<br />
  &lt;/FilesMatch&gt;<br />
  - cache text, css, and javascript files for one week<br />
  &lt;FilesMatch &quot;.(js|css|pdf|txt)$&quot;&gt;<br />
  Header set Cache-Control &quot;max-age=604800&quot;<br />
  &lt;/FilesMatch&gt;<br />
  - cache html and htm files for one day<br />
  &lt;FilesMatch &quot;.(html|htm)$&quot;&gt;<br />
  Header set Cache-Control &quot;max-age=43200&quot;<br />
  &lt;/FilesMatch&gt;<br />
  - implement minimal caching during site development<br />
  &lt;FilesMatch &quot;\.(flv|gif|jpg|jpeg|png|ico|js|css|pdf|swf|html|h tm|txt)$&quot;&gt;<br />
  Header set Cache-Control &quot;max-age=5&quot;<br />
  &lt;/FilesMatch&gt;<br />
  - explicitly disable caching for scripts and other dynamic files<br />
  &lt;FilesMatch &quot;\.(pl|php|cgi|spl|scgi|fcgi)$&quot;&gt;<br />
  Header unset Cache-Control<br />
  &lt;/FilesMatch&gt;<br />
  - alternate method for file caching<br />
  ExpiresActive On<br />
  ExpiresDefault A604800 - 1 week<br />
  ExpiresByType image/x-icon A2419200 - 1 month<br />
  ExpiresByType application/x-javascript A2419200 - 1 month<br />
  ExpiresByType text/css A2419200 - 1 month<br />
  ExpiresByType text/html A300 - 5 minutes<br />
  - disable caching for scripts and other dynamic files<br />
  &lt;FilesMatch &quot;\.(pl|php|cgi|spl|scgi|fcgi)$&quot;&gt;<br />
  ExpiresActive Off<br />
  &lt;/FilesMatch&gt;<br />
</p>
<p>* Convert common time intervals into seconds:<br />
  300 = 5 minutes<br />
  2700 = 45 minutes<br />
  3600 = 1 hour<br />
  54000 = 15 hours<br />
  86400 = 1 day<br />
  518400 = 6 days<br />
  604800 = 1 week<br />
  1814400 = 3 weeks<br />
  2419200 = 1 month<br />
  26611200 = 11 months<br />
  29030400 = 1 year = never expires<br />
</p>
<p><strong>3.8. Cài đặt ngôn ngữ và kiểu mã hóa mặc định</strong></p>
<p>- set the default language<br />
  DefaultLanguage en-US<br />
  - set the default character set<br />
  AddDefaultCharset UTF-8</p>
<p><strong>3.9. Mô tả MIME</strong></p>
<p>MIME types là tập các phần mở rộng của file, server cần biết tham số này để biết nó đang thao tác với loại file nào. Sử dụng “AddType” để thêm một MIME, tham số tiếp theo là loại MIME và cuối cùng là phần mở rộng của file. Ví dụ với file MP3 hoặc SWF:</p>
<p>AddType application/x-shockwave-flash swf<br />
  AddType application/x-shockwave-flash .swf<br />
  AddType video/x-flv .flv<br />
  AddType image/x-icon .ico</p>
<p>Một số loại file không cho chạy trực tiếp trên trình duyệt mà yêu cầu download về máy, loại MIME cần thiết lập là: application/octec-stream</p>
<p>Danh sách các MIME và loại file tương ứng:</p>
<p>AddType text/html .html .htm<br />
  AddType text/plain .txt<br />
  AddType text/richtext .rtx<br />
  AddType text/tab-separated-values .tsv<br />
  AddType text/x-setext .etx<br />
  AddType text/x-server-parsed-html .shtml .sht<br />
  AddType application/macbinhex-40 .hqx<br />
  AddType application/netalivelink .nel<br />
  AddType application/netalive .net<br />
  AddType application/news-message-id<br />
  AddType application/news-transmission<br />
  AddType application/octet-stream .bin .exe<br />
  AddType application/oda .oda<br />
  AddType application/pdf .pdf<br />
  AddType application/postscript .ai .eps .ps<br />
  AddType application/remote-printing<br />
  AddType application/rtf .rtf<br />
  AddType application/slate<br />
  AddType application/zip .zip<br />
  AddType application/x-mif .mif<br />
  AddType application/wita<br />
  AddType application/wordperfect5.1<br />
  AddType application/x-csh .csh<br />
  AddType application/x-dvi .dvi<br />
  AddType application/x-hdf .hdf<br />
  AddType application/x-latex .latex<br />
  AddType application/x-netcdf .nc .cdf<br />
  AddType application/x-sh .sh<br />
  AddType application/x-tcl .tcl<br />
  AddType application/x-tex .tex<br />
  AddType application/x-texinfo .texinfo .texi<br />
  AddType application/x-troff .t .tr .roff<br />
  AddType application/x-troff-man .man<br />
  AddType application/x-troff-me .me<br />
  AddType application/x-troff-ms .ms<br />
  AddType application/x-wais-source .src<br />
  AddType application/x-bcpio .bcpio<br />
  AddType application/x-cpio .cpio<br />
  AddType application/x-gtar .gtar<br />
  AddType application/x-shar .shar<br />
  AddType application/x-sv4cpio .sv4cpio<br />
  AddType application/x-sv4crc .sv4crc<br />
  AddType application/x-tar .tar<br />
  AddType application/x-ustar .ustar<br />
  AddType application/x-director .dcr<br />
  AddType application/x-director .dir<br />
  AddType application/x-director .dxr<br />
  AddType application/x-onlive .sds<br />
  AddType application/x-httpd-cgi .cgi<br />
  AddType image/gif .gif .GIF<br />
  AddType image/ief .ief<br />
  AddType image/jpeg .jpeg .jpg .jpe .JPG<br />
  AddType image/tiff .tiff .tif<br />
  AddType image/x-cmu-raster .ras<br />
  AddType image/x-portable-anymap .pnm<br />
  AddType image/x-portable-bitmap .pbm<br />
  AddType image/x-portable-graymap .pgm<br />
  AddType image/x-portable-pixmap .ppm<br />
  AddType image/x-rgb .rgb<br />
  AddType image/x-xbitmap .xbm<br />
  AddType image/x-xpixmap .xpm<br />
  AddType image/x-xwindowdump .xwd<br />
  AddType audio/basic .au .snd<br />
  AddType audio/x-aiff .aif .aiff .aifc<br />
  AddType audio/x-wav .wav<br />
  AddType audio/x-pn-realaudio .ram<br />
  AddType audio/x-midi .mid<br />
  AddType video/mpeg .mpeg .mpg .mpe<br />
  AddType video/quicktime .qt .mov<br />
  AddType video/x-msvideo .avi<br />
  AddType video/x-sgi-movie .movie<br />
  AddType message/external-body<br />
  AddType message/news<br />
  AddType message/partial<br />
  AddType message/rfc822<br />
  AddType multipart/alternative<br />
  AddType multipart/appledouble<br />
  AddType multipart/digest<br />
  AddType multipart/mixed<br />
  AddType multipart/parallel<br />
  AddType x-world/x-vrml .wrl</p>
<p><strong>3.10. Gửi kiểu mã hóa và header không cần thẻ meta</strong></p>
<p>- send the language tag and default character set<br />
  - AddType 'text/html; charset=UTF-8' html<br />
  AddDefaultCharset UTF-8<br />
  DefaultLanguage en-US</p>
<p><strong>3.11. Giới hạn các request GET và PUT</strong><br />
  - limit server request methods to GET and PUT<br />
  Options -ExecCGI -Indexes -All<br />
  RewriteEngine on<br />
RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK|OPTIONS|HEAD) RewriteRule .* - [F]</p>
<p><strong>3.12. Lựa chọn file xử lý theo phương thức request tới server</strong><br />
  - process files according to server request method<br />
  Script PUT /cgi-bin/upload.cgi<br />
Script GET /cgi-bin/download.cgi</p>
<p><strong>3.13. Thực thi một định dạng file bằng 1 cgi script</strong><br />
</p>
<p>- execute all png files via png-script.cgi<br />
  Action image/png /cgi-bin/png-script.cgi<br />
  <br />
  <strong>4. Các cấu hình bảo mật<br />
  </strong><strong>4.1. Ngăn cản truy cập file .htaccess</strong></p>
<p>Khi người dùng cố tình truy nhập file .htaccess sẽ trả về lỗi 403, có nhiều cách để cấu hình, có thể cấu hình file với CHMOD là 644 hoặc thêm đoạn mã sau:</p>
<p>- secure htaccess file<br />
  &lt;Files .htaccess&gt;<br />
  order allow,deny<br />
  deny from all<br />
  &lt;/Files&gt;</p>
<p><strong>4.2. Ngăn cản truy cập tới một file đặc biệt</strong></p>
<p>Để chặn truy nhập vào một file đặc biệt nào đó, thêm đoạn mã sau vào file .htaccess, giả sử là file secretfile.jpg</p>
<p>- prevent viewing of a specific file<br />
  &lt;files secretfile.jpg&gt;<br />
  order allow,deny<br />
  deny from all<br />
  &lt;/files&gt;</p>
<p><strong>4.3. Chặn truy cập tới nhiều file</strong></p>
<p>&lt;FilesMatch &quot;\.(htaccess|htpasswd|ini|phps|fla|psd|log|sh) $&quot;&gt;<br />
  Order Allow,Deny<br />
  Deny from all<br />
  &lt;/FilesMatch&gt;</p>
<p><strong>4.4. Chống browse thư mục trái phép</strong></p>
<p>Đảm bảo người dùng không có đủ quyền không thể xem toàn bộ trang web dưới dạng Directory listing.</p>
<p>- disable directory browsing<br />
  Options All –Indexes</p>
<p>Ngược lại để cho phép người dùng có thể xem dưới dạng này, sử dụng:</p>
<p>- enable directory browsing<br />
  Options All +Indexes</p>
<p>Ngăn cản server listing directory:</p>
<p>- prevent folder listing<br />
  IndexIgnore *</p>
<p>Ngăn cản truy nhập vào các file có định dạng nào đó, sử dụng IndexIgnore</p>
<p>- prevent display of select file types<br />
  IndexIgnore *.wmv *.mp4 *.avi *.etc</p>
<p><strong>4.5. Thay đổi trang index mặc định</strong></p>
<p>Có thể thay vì sử dụng trang index một cách mặc định, ta cấu hình cho server nhận một file khác có chức năng tương tự như file index (ở đâylà business.html)</p>
<p>- serve alternate default index page<br />
  DirectoryIndex business.html</p>
<p>Hoặc cho một loạt file đều có thể là file index, server sẽ tìm kiếm và đưa ra file đầu tiên tìm được là file index</p>
<p>- serve first available alternate default index page from series<br />
  DirectoryIndex filename.html index.cgi index.pl default.htm</p>
<p><strong>4.6. Ngụy trang cho định dạng script</strong></p>
<p>Để tăng cường tính bảo mật, việc ngụy trang cho ngôn ngữ kịch bản bằng việc thay đổi phần mở rộng cũng là một yếu tố cần xét đến:</p>
<p>- serve foo files as php files<br />
  AddType application/x-httpd-php .foo</p>
<p>- serve foo files as cgi files<br />
  AddType application/x-httpd-cgi .foo</p>
<p><strong>4.7. Giới hạn truy cập tới mạng LAN</strong></p>
<p>- limit access to local area network<br />
  &lt;Limit GET POST PUT&gt;<br />
  order deny,allow<br />
  deny from all<br />
  allow from 192.168.0.0/33<br />
  &lt;/Limit&gt;</p>
<p><strong>4.8. Bảo vệ thư mục bằng địa chỉ IP và/hoặc domain</strong></p>
<p>Cấu hình cho phép các truy cập ngoại trừ truy cập từ địa chỉ: x.y.z.v và từ domain.com</p>
<p>- allow all except those indicated here<br />
  &lt;Limit GET POST PUT&gt;<br />
  order allow,deny<br />
  allow from all<br />
  deny from x.y.z.v<br />
  deny from .*domain\.com.*<br />
  &lt;/Limit&gt;</p>
<p>Ngược lại với cấu hình bên trên, từ chối tất cả IP truy cập ngoại trừ x.y.z.v và domain.com</p>
<p>- deny all except those indicated here<br />
  &lt;Limit GET POST PUT&gt;<br />
  order deny,allow<br />
  deny from all<br />
  allow from x.y.z.v<br />
  allow from .*domain\.com.*<br />
  &lt;/Limit&gt;</p>
<p>Ngoài ra, cũng có thể tiết kiệm băng thông bằng cách block một số định dạng file đặc biệt như: .jpg, .zip, ,mp3, … từ các server ngoài (ở đây là abc và xyz)</p>
<p>- block visitors referred from indicated domains<br />
  &lt;IfModule mod_rewrite.c&gt;<br />
  RewriteEngine on<br />
  RewriteCond %{HTTP_REFERER} abc\.com [NC,OR]<br />
  RewriteCond %{HTTP_REFERER} xyz\.com [NC,OR]<br />
  RewriteRule .* - [F]<br />
  &lt;/ifModule&gt;</p>
<p><strong>4.9. Ngăn cản hoặc cho phép truy cập domain theo dải địa chỉ IP</strong></p>
<p>Có nhiều phương pháp để block một dải địa chỉ IP bằng cách cấu hình .htaccess. Cách thức đầu tiên có thể sử dụng sô CIDR (Classess Inter-Domain Routing) của dải IP, cách này hiệu quả để block các mega-spammer như RIPE, Optinet, …</p>
<p>- block IP range by CIDR number<br />
  &lt;Limit GET POST PUT&gt;<br />
  order allow,deny<br />
  allow from all<br />
  deny from 10.1.0.0/16<br />
  deny from 80.0.0/8<br />
  &lt;/Limit&gt;</p>
<p>Để cho phép bởi CIDR:</p>
<p>- allow IP range by CIDR number<br />
  &lt;Limit GET POST PUT&gt;<br />
  order deny,allow<br />
  deny from all<br />
  allow from 10.1.0.0/16<br />
  allow from 80.0.0/8<br />
  &lt;/Limit&gt;</p>
<p>Một biện pháp khác chúng ta có thể block dải IP đầu vào liên quan tới số truncating cho tới khi dải mong muốn xuất hiện</p>
<p>- block IP range by address truncation<br />
  &lt;Limit GET POST PUT&gt;<br />
  order allow,deny<br />
  allow from all<br />
  deny from 99.88.77.66<br />
  deny from 99.88.77.*<br />
  deny from 99.88.*.*<br />
  deny from 99.*.*.*<br />
  &lt;/Limit&gt;</p>
<p>Cho phép địa chỉ IP theo cách này:</p>
<p>- allow IP range by address truncation<br />
  &lt;Limit GET POST PUT&gt;<br />
  order deny,allow<br />
  deny from all<br />
  allow from 99.88.77.66<br />
  allow from 99.88.77.*<br />
  allow from 99.88.*.*<br />
  allow from 99.*.*.*<br />
  &lt;/Limit&gt;</p>
<p><strong>4.10. Chặn hoặc cho phép nhiều địa chỉ trong cùng 1 dòng</strong></p>
<p>Block:</p>
<p>- block two unique IP addresses<br />
  deny from 99.88.77.66 11.22.33.44<br />
  - block three ranges of IP addresses<br />
  deny from 99.88 99.88.77 11.22.33</p>
<p>Allow:</p>
<p>- allow two unique IP addresses<br />
  allow from 99.88.77.66 11.22.33.44<br />
  - allow three ranges of IP addresses<br />
  allow from 99.88 99.88.77 11.22.33</p>
<p><strong>4.11. Các luật khác sử dụng để block hay allow địa chỉ IP</strong></p>
<p>Có một số luật khác có thể sử dụng:</p>
<p>- block a partial domain via network/netmask values<br />
  deny from 99.1.0.0/255.255.0.0</p>
<p>- block a single domain<br />
  deny from 99.88.77.66</p>
<p>- block domain.com but allow sub.domain.com<br />
  order deny,allow<br />
  deny from domain.com<br />
  allow from sub.domain.com</p>
<p><strong>4.12. Ngừng các hotlinking, luân chuyển nội dung server</strong></p>
<p>Mục tiêu nhằm giúp các quản trị viên ngăn cản các website bên ngoài sử dụng trực tiếp các hình ảnh, nội dung, link, … từ website của mình. Vì dạng này làm tốn băng thông.<br />
  Sử dụng chế độ này khi đã kích hoạt mod_rewrite.</p>
<p>- stop hotlinking and serve alternate content<br />
  &lt;IfModule mod_rewrite.c&gt;<br />
  RewriteEngine on<br />
  RewriteCond %{HTTP_REFERER} !^$<br />
  RewriteCond %{HTTP_REFERER} !^http://(www\.)?domain\.com/.*$ [NC]<br />
  RewriteRule .*\.(gif|jpg)$ http://www.domain.com/eatme.jpg [R,NC,L]<br />
  &lt;/ifModule&gt;</p>
<p>Để chuyển giao một page lỗi thay vì một số hình ảnh như eatme.jpg như bên trên, thay dòng RewriteRule bằng dòng:</p>
<p>- serve a standard 403 forbidden error page<br />
  RewriteRule .*\.(gif|jpg)$ - [F,L]</p>
<p>Để cho phép một domain ngoài có thể sử dụng hotlinking (goodsite chẳng hạn), thêm dòng cấu hình:</p>
<p>- allow linking from the following site<br />
  RewriteCond %{HTTP_REFERER} !^http://(www\.)?goodsite\.com/.*$ [NC]</p>
<p><strong>4.13. Chặn Evil Robots, Site Rippers, và Offline Browsers</strong><br />
  RewriteEngine On<br />
  RewriteCond %{HTTP_USER_AGENT} ^BlackWidow [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Bot\ mailto:craftbot@yahoo.com [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^ChinaClaw [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Custo [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^DISCo [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Download\ Demon [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^eCatch [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^EirGrabber [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^EmailSiphon [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^EmailWolf [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Express\ WebPictures [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^ExtractorPro [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^EyeNetIE [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^FlashGet [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^GetRight [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^GetWeb! [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Go!Zilla [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Go-Ahead-Got-It [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^GrabNet [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Grafula [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^HMView [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} HTTrack [NC,OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Image\ Stripper [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Image\ Sucker [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} Indy\ Library [NC,OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^InterGET [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Internet\ Ninja [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^JetCar [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^JOC\ Web\ Spider [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^larbin [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^LeechFTP [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Mass\ Downloader [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^MIDown\ tool [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Mister\ PiX [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Navroad [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^NearSite [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^NetAnts [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^NetSpider [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Net\ Vampire [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^NetZIP [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Octopus [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Offline\ Explorer [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Offline\ Navigator [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^PageGrabber [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Papa\ Foto [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^pavuk [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^pcBrowser [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^RealDownload [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^ReGet [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^SiteSnagger [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^SmartDownload [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^SuperBot [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^SuperHTTP [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Surfbot [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^tAkeOut [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Teleport\ Pro [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^VoidEYE [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Web\ Image\ Collector [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Web\ Sucker [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebAuto [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebCopier [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebFetch [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebGo\ IS [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebLeacher [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebReaper [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebSauger [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Website\ eXtractor [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Website\ Quester [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebStripper [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebWhacker [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WebZIP [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Wget [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Widow [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^WWWOFFLE [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Xaldon\ WebSpider [OR]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Zeus<br />
RewriteRule ^.* - [F,L]</p>
<p>Thay vì gửi một thông báo thân thiện, có thể gửi lại mộ website:</p>
<p>- send em to a hellish website of your choice<br />
  RewriteRule ^.*$ http://www.hellish-website.com [R,L]</p>
<p>Hoặc gửi một blackhold fake email:</p>
<p>- send em to a virtual blackhole of fake email addresses<br />
  RewriteRule ^.*$ http://english-61925045732.spampoison.com [R,L]</p>
<p>Có thể chặn theo referrer, ở đây ta chặn iaea.org:</p>
<p>RewriteCond %{HTTP_REFERER} ^http://www.iaea.org$<br />
  RewriteRule !^http://[^/.]\.yourdomain\.com.* - [F,L]</p>
<p>Một số cách chặn khác:</p>
<p>- redirect any request for anything from spamsite to differentspamsite<br />
  RewriteCond %{HTTP_REFERER} ^http://.*spamsite.*$ [NC]<br />
  RewriteRule .* http://www.differentspamsite.com [R]</p>
<p>- redirect all requests from spamsite to an image of something at differentspamsite<br />
  RewriteCond %{HTTP_REFERER} ^http://.*spamsite.*$ [NC]<br />
  RewriteRule .* http://www.differentspamsite/something.jpg [R]</p>
<p>- redirect traffic from a certain address or range of addresses to another site<br />
  RewriteCond %{REMOTE_ADDR} 192.168.10.*<br />
  RewriteRule .* http://www.differentspamsite.com/index.html [R]</p>
<p><strong>4.14. Pass bảo vệ</strong></p>
<p>Đặt password bảo vệ là một biện pháp bảo vệ nội dung website và chỉ cho phép người dùng nội bộ có thể truy nhập nội dung.<br />
  Được hỗ trợ bởi Apache. Giúp giới hạn người dùng trong những khu vực khác nhau của một website.<br />
  Khi một thư mục được đặt password thì toàn bộ thư mục con và file trong thư mục sẽ được đặt password như vậy.<br />
  Nội dung file .htaccess để thư mục chứa nó được bảo vệ bởi mật khẩu:</p>
<p>username:encryptedpassword<br />
  fred_smithCF9Pam/MXJg2</p>
<p>Tham khảo trang sau (tạo password bảo vệ thư mục):</p>
<p>http://www.thejackol.com/scripts/htpasswdgen.php</p>
<p>- password-protect single file<br />
  &lt;Files secure.php&gt;<br />
  AuthType Basic<br />
  AuthName &quot;Prompt&quot;<br />
  AuthUserFile /home/path/.htpasswd<br />
  Require valid-user<br />
  &lt;/Files&gt;</p>
<p>- password-protect multiple files<br />
  &lt;FilesMatch &quot;^(execute|index|secure|insanity|biscuit)*$&quot;&gt;<br />
  AuthType basic<br />
  AuthName &quot;Development&quot;<br />
  AuthUserFile /home/path/.htpasswd<br />
  Require valid-user<br />
  &lt;/FilesMatch&gt;</p>
<p>- password-protect the directory in which this htaccess rule resides<br />
  AuthType basic<br />
  AuthName &quot;This directory is protected&quot;<br />
  AuthUserFile /home/path/.htpasswd<br />
  AuthGroupFile /dev/null<br />
  Require valid-user</p>
<p>- password-protect directory for every IP except the one specified<br />
  - place in htaccess file of a directory to protect that entire directory<br />
  AuthType Basic<br />
  AuthName &quot;Personal&quot;<br />
  AuthUserFile /home/path/.htpasswd<br />
  Require valid-user<br />
  Allow from 99.88.77.66<br />
  Satisfy Any</p>
<p><strong>4.15. Tự động đặt CHMOD cho các loại file</strong></p>
<p>Cách thức này đảm bảo đặt CHMOD cho các loại file xác định.</p>
<p>- ensure CHMOD settings for specified file types<br />
  - remember to never set CHMOD 777 unless you know what you are doing<br />
  - files requiring write access should use CHMOD 766 rather than 777<br />
  - keep specific file types private by setting their CHMOD to 400<br />
  chmod .htpasswd files 640<br />
  chmod .htaccess files 644<br />
  chmod php files 600</p>
<p><strong>4.16. Ngụy trang tất cả các định dạng mở rộng</strong></p>
<p>Ngụy trang tất cả các file và coi như file .php</p>
<p>- diguise all file extensions as php<br />
  ForceType application/x-httpd-php</p>
<p>Hoặc như các định dạng khác. Ngoài ra, có thể che giấu file php dưới các định dạng khác:</p>
<p>&lt;FilesMatch &quot;\.(htm|html|php)$&quot;&gt;<br />
  SetHandler application/x-httpd-php<br />
  &lt;/FilesMatch&gt;</p>
<p><strong>4.17. Chống tấn công từ chối dịch vụ bằng cách giới hạn kích thước file upload</strong></p>
<p>- protect against DOS attacks by limiting file upload size<br />
  LimitRequestBody 10240000</p>
<p><strong>4.18. Bảo vệ thư mục bằng cách disable việc thực thi các script</strong></p>
<p>- secure directory by disabling script execution<br />
  AddHandler cgi-script .php .pl .py .jsp .asp .htm .shtml .sh .cgi<br />
  Options –ExecCGI</p>
<p><strong>4.19. Yêu cầu SSL</strong></p>
<p>- require SSL<br />
  SSLOptions +StrictRequire<br />
  SSLRequireSSL<br />
  SSLRequire %{HTTP_HOST} eq &quot;domain.tld&quot;<br />
  ErrorDocument 403 https://domain.tld</p>
<p>- require SSL without mod_ssl<br />
  RewriteCond %{HTTPS} !=on [NC]<br />
  RewriteRule ^.*$ https://%{SERVER_NAME}%{REQUEST_URI} [R,L]</p>
<p><strong>5. Một số cấu hình hữu ích khác</strong></p>
<p><strong>5.1. Kiểm tra URL</strong></p>
<p>- automatically corect simple speling erors<br />
  &lt;IfModule mod_speling.c&gt;<br />
  CheckSpelling On<br />
  &lt;/IfModule&gt;</p>
<p><strong>5.2. Sắp xếp lại trang thông báo lỗi</strong></p>
<p>Cấu hình này rất hữu ích vì nó đưa ra lỗi cho người truy cập website một cách thân thiện, giúp cho chủ website hiện thị các thông báo lỗi theo cách riêng.</p>
<p>- serve custom error pages<br />
  ErrorDocument 400 /errors/400.html<br />
  ErrorDocument 401 /errors/401.html<br />
  ErrorDocument 403 /errors/403.html<br />
  ErrorDocument 404 /errors/404.html<br />
  ErrorDocument 500 /errors/500.html</p>
<p><strong>5.3. Chỉ dẫn cho browser download về máy thay vì chạy trực tiếp</strong></p>
<p>Điều này hữu ích đối với các file multi media</p>
<p>- instruct browser to download multimedia files<br />
  AddType application/octet-stream .avi<br />
  AddType application/octet-stream .mpg<br />
  AddType application/octet-stream .wmv<br />
  AddType application/octet-stream .mp3<br />
  Có thể áp dụng với các định dạng khác (Xem thêm phần: 3.9)</p>
<p><strong>5.4. Chỉ thị server hiển thị mã nguồn với một số file thực thi</strong></p>
<p>Một số trường hợp cần hiển thị mã nguồn của một file thay vì thực thi chúng, sử dụng:<br />
  RemoveHandler cgi-script .pl .py .cgi</p>
<p><strong>5.5. Redirect người dùng tới một site tạm thời khi phát triển hoặc sửa lỗi</strong></p>
<p>Trong quá trình phát triển, bảo trì hay sửa chữa website, bạn không muốn khách hàng viếng thăm, cấu hình dưới sẽ giúp chuyển hướng người dùng tới một site khác trong khi quản trị viên vẫn có khả năng truy nhập đầy đủ (x.x.x.x là IP của quản trị):</p>
<p>- redirect all visitors to alternate site but retain full access for you<br />
  ErrorDocument 403 http://www.alternate-site.com<br />
  Order deny,allow<br />
  Deny from all<br />
  Allow from x.x.x.x</p>
<p><strong>5.6. Chặn truy cập tới file hay thư mục theo thời gian</strong><br />
  - prevent access during the midnight hour<br />
  RewriteCond %{TIME_HOUR} ^12$<br />
RewriteRule ^.*$ - [F,L]</p>
<p>- prevent access throughout the afternoon<br />
  RewriteCond %{TIME_HOUR} ^(12|13|14|15)$<br />
  RewriteRule ^.*$ - [F,L]<br />
  <strong>6. Thủ thuật redirect</strong></p>
<p>Đối với tất cả các loại redirect sử dụng mode_rewrite cần enable chế độ: RewriteEngine.</p>
<p>- initialize and enable rewrite engine<br />
  RewriteEngine on</p>
<p><strong>6.1. Redirect từ http://www.domain.com sang http://domain.com</strong></p>
<p>- permanently redirect from www domain to non-www domain<br />
  RewriteEngine on<br />
  Options +FollowSymLinks<br />
  RewriteCond %{HTTP_HOST} ^www\.domain\.tld$ [NC]<br />
  RewriteRule ^(.*)$ http://domain.tld/$1 [R=301,L]</p>
<p><strong>6.2. Redirect từ một domain cũ sang domain mới</strong></p>
<p>- redirect from old domain to new domain<br />
  RewriteEngine On<br />
  RewriteRule ^(.*)$ http://www.new-domain.com/$1 [R=301,L]</p>
<p><strong>6.3. Redirect “String Variations” sang một địa chỉ</strong></p>
<p>Giả sử một request có chứa string: “some-string”, ta sẽ chuyển request này tới trang: http://some-string.com</p>
<p>- redirect any variations of a specific character string to a specific address<br />
  RewriteRule ^some-string http://www.some-string.com [R]</p>
<p>Một số phương pháp khác:</p>
<p>- map URL variations to the same directory on the same server<br />
  AliasMatch ^/director(y|ies) /www/docs/target</p>
<p>- map URL variations to the same directory on a different server<br />
  RedirectMatch ^/[dD]irector(y|ies) http://domain.com</p>
<p><strong>6.4. Một số redirect khác</strong></p>
<p>Redirect một site đầu vào với trạng thái 301:</p>
<p>- redirect an entire site via 301<br />
  redirect 301 / http://www.domain.com/</p>
<p>Redirect một file với trạng thái 301:</p>
<p>- redirect a specific file via 301<br />
  redirect 301 /current/currentfile.html http://www.newdomain.com/new/newfile.html</p>
<p>Redirect một site qua một redirect liên tục:</p>
<p>- redirect an entire site via permanent redirect<br />
  Redirect permanent / http://www.domain.com/</p>
<p>Redirect một trang hoặc một thư mục với redirect liên tục:</p>
<p>- redirect a page or directory<br />
  Redirect permanent old_file.html http://www.new-domain.com/new_file.html<br />
  Redirect permanent /old_directory/ http://www.new-domain.com/new_directory/</p>
<p>Redirect một file sử dụng RedirectMatch:</p>
<p>- redirect a file using RedirectMatch<br />
  RedirectMatch 301 ^.*$ http://www.domain.com/index.html</p>
<p>Khi redirect các file, sử dụng luật Redirect với các file trong cùng domain, sử dụng luật RewriteRule cho bất cứ domain nào. Luật RewriteRule mạnh hơn luật Redirect.</p>
<p>- redirect files directories and domains via RewriteRule<br />
  RewriteRule http://old-domain.com/old-file.htmlhttp://new-domain.com/new-file.html<br />
  RewriteRule http://old-domain.com/old-dir/http://new-domain.com/new-dir/<br />
  RewriteRule http://old-domain.com/http://new-domain.com/</p>
<p><strong>6.5. Chuyển khách hàng tới một domain con</strong></p>
<p>Luật này cho phép tất cả các visitor xem page thông qua domain con.</p>
<p>- send visitors to a subdomain<br />
  RewriteCond %{HTTP_HOST} !^$<br />
  RewriteCond %{HTTP_HOST} !^subdomain\.domain\.com$ [NC]<br />
  RewriteRule ^/(.*)$ http://subdomain.domain.tld/$1 [L,R=301]</p>
<p><strong>6.6. Một số redirect khác</strong><br />
</p>
<p>- rewrite only if the file is not found<br />
  RewriteCond %{REQUEST_FILENAME} !-f<br />
  RewriteRule ^(.+)special\.html?$ cgi-bin/special/special-html/$1</p>
<p><strong>- rewrite only if an image is not found</strong><br />
  RewriteCond %{REQUEST_FILENAME} !-f<br />
RewriteRule images/special/(.*).gif cgi-bin/special/mkgif?$1</p>
<p><strong>- seo-friendly rewrite rules for various directories</strong><br />
  RewriteRule ^(.*)/aud/(.*)$ $1/audio-files/$2 [L,R=301]<br />
  RewriteRule ^(.*)/img/(.*)$ $1/image-files/$2 [L,R=301]<br />
  RewriteRule ^(.*)/fla/(.*)$ $1/flash-files/$2 [L,R=301]<br />
RewriteRule ^(.*)/vid/(.*)$ $1/video-files/$2 [L,R=301]</p>
<p><strong>- broswer sniffing via htaccess environmental variables</strong><br />
  RewriteCond %{HTTP_USER_AGENT} ^Mozilla.*<br />
  RewriteRule ^/$ /index-for-mozilla.html [L]<br />
  RewriteCond %{HTTP_USER_AGENT} ^Lynx.*<br />
  RewriteRule ^/$ /index-for-lynx.html [L]<br />
RewriteRule ^/$ /index-for-all-others.html [L]</p>
<p><strong>- redirect query to Google search</strong><br />
  Options +FollowSymlinks<br />
  RewriteEngine On<br />
  RewriteCond %{REQUEST_URI} .google\.php*<br />
RewriteRule ^(.*)$ ^http://www.google.com/search?q=$1 [R,NC,L]</p>
<p>- deny request according to the request method<br />
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK|OPTIONS|HEAD)$ [NC]<br />
  RewriteRule ^.*$ - [F]</p>
<p>- redirect uploads to a better place<br />
  RewriteCond %{REQUEST_METHOD} ^(PUT|POST)$ [NC]<br />
  RewriteRule ^(.*)$ /cgi-bin/upload-processor.cgi?p=$1 [L,QSA]</p>
<p>- seo friendly redirect for a single file<br />
  Redirect 301 /old-dir/old-file.html http://domain.com/new-dir/new-file.html</p>
<p>- seo friendly redirect for multiple files</p>
<p>- redirects all files in dir directory with first letters xyz<br />
  RedirectMatch 301 /dir/xyz(.*) http://domain.com/$1</p>
<p>- seo friendly redirect entire site to a different domain<br />
  Redirect 301 / http://different-domain.com</p>
<p><strong>7. Một số cấu hình khác</strong></p>
<p><strong>7.1. Kích hoạt SSI</strong></p>
<p>Khi sử dụng chế độ SSI, phần mở rộng các file trên server phải ở dạng .shtml thay vì .html. Điều này gây bất lợi cho các website đã thiết lập dạng .html, để tránh phải chuyển đổi lại định dạng mở rộng file trên server, tạo file .htaccess với nội dung:</p>
<p>AddHandler server-parsed .html</p>
<p>Có thể thêm nhiều dòng để server chấp nhận nhiều định dạng khác nhau.<br />
  Ví dụ:</p>
<p>AddHandler server-parsed .html<br />
  AddHandler server-parsed .shtml<br />
  AddHandler server-parsed .htm</p>
<p><strong>7.2. Chặn truy cập tới các file include trong file .php</strong></p>
<p>Để tránh bị truy cập tới thư mục chứa các file .php, tạo file .htaccess với nội dung:</p>
<p>-- Enable Mod Rewrite, this is only required once in each .htaccess file<br />
  RewriteEngine On<br />
  RewriteBase /<br />
  -- Test for access to includes directory<br />
  RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /includes/ .*$ [NC]<br />
  -- Test that file requested has php extension<br />
  RewriteCond %{REQUEST_FILENAME} ^.+\.php$<br />
  -- Forbid Access<br />
  RewriteRule .* - [F,NS,L]</p>
<p>Trong đó, includes là thư mục chứa file .php</p>

