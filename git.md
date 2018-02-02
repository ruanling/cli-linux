1. git remote add origin https://github.com/..
2. git add --all
3. git commit -m "<Message>"
4. git push <alias> <branch_name>
5. git clone https://github.com/user/repository.git

<div>
<p>Sự quan trọng của quản lý phiên bản (Git) hiện nay trong lập trình là không thể chối cãi. Lúc mới tập tành xài Git, nó thật rối rắm và phức tạp bởi vì phải dùng đến các dòng lệnh command line.</p>
<p>Sau một thời gian sử dụng, mình đã ước &ldquo;<em>Sẽ thật là hay nếu như có một danh sách các lệnh được sử dụng thường xuyên để ghi nhớ thay vì lan man phải nhớ hết tất cả các lệnh</em>&ldquo;. Mỗi khi gặp vấn đề gì đó cơ bản về github, mình thường lên stackoverflow tìm kiếm, sau đó copy paste và không cần hiểu quá sâu xa, quá rõ ràng về cơ chế hoạt động của nó. Nhưng mình nhận ra tình trạng này lâu dài chỉ làm cho kỹ năng của mình yếu dần đi.</p>
<p>Trong một năm đi làm, danh sách các lệnh này theo mình qua hầu như các dự án. Có thể nó không đầy đủ nhưng về cơ bản ai cũng chỉ cần có vậy, thậm chí các leader sẽ dùng nhiều rất nhiều vài lệnh mà mình sắp trình bày đây.<span id="more-580"> </span></p>
<h2>Lệnh cơ bản, bộ ba pháp thuật</h2>
<p>96,69% ai sử dụng Git đều từng dùng đó là:</p>
<pre>git add --all    git commit -m &quot;&lt;Message&gt;&quot;    git push &lt;alias&gt; &lt;branch_name&gt;</pre>
<p>Nhưng đó là 3 lệnh quá cơ bản chỉ phù hợp khi dùng trong dự án cá nhân khi mà bạn chỉ có nhu cầu lưu trữ code. Khi làm việc với dự án cần tính ổn định và khả năng bảo trì thì bạn cần nhiều hơn thế, đặc biệt là sức mạnh phân nhánh của Git.</p>
<p>Ví dụ bạn có 1 folder tên <strong>xxx</strong>, trong đó có 1 file <strong>linkphim.txt</strong>. Vì bạn sợ đến một ngày đẹp trời máy bạn hư hoặc bị thằng cờ hó nào đó trộm mất thì bạn sẽ bị mất hết phim hay, diễn viên đẹp mà bạn ngày ngày cất công tìm kiếm và bổ sung vào đó. Bạn phải đẩy nó lên Github để lưu trữ lại và để làm được điều đó, bạn cần biến cái folder đó thành một kho lưu trữ local với lệnh đơn giản</p>
<pre>git init</pre>
<p>Nếu bạn sử dụng Github và có 1 repository ở trên đó thì nó được gọi là remote repository (kho lưu trữ từ xa, khác với kho lưu trữ local trong máy bạn). Tên <strong>alias</strong> mặc định của remote repository là <strong>origin. </strong>Còn làm sao tạo remote repository thì chỉ cần vô <a href="https://github.com/" target="_blank" rel="noopener noreferrer">github.com</a> đăng nhập và <strong>New repository</strong> thôi. Sau khi tạo xong nhớ copy cái link nó sinh ra. Chẳng hạn mình tạo repository tên tokyoangel thì nó sinh ra link này</p>
<pre>https://github.com/viethuong/tokyoangel.git</pre>
<p>Bây giờ có kho lưu trữ local rồi, có kho lưu trữ online rồi thì làm sao đẩy dữ liệu lên. Đơn giản, mở Git bash chạy lệnh này là được</p>
<pre>git remote add origin https://github.com/viethuong/tokyoangel.git  </pre>
<p>Đến đây thì bạn đã map được local repository và remote repository rồi, mở Git bash và thực hiện bộ ba pháp thuật ở trên thử được chưa. Chưa được thì đi chết đi.</p>
<p>Chưa chết thì làm tiếp, ahihi. Bây giờ mình muốn copy cục source hay hay của thằng nào đó, cách đơn giản là dùng</p>
<pre>git clone &lt;link repository muốn ăn cắp&gt;</pre>
<p>để sao chép cục source đó về máy.</p>
<p>Nhưng tính chất trẻ trâu nổi dậy, bạn muốn đẩy nó lên git của bạn chứ không phải remote từ git của thằng đó, mà đúng hơn là nếu remote từ git của thằng đó thì bạn sẽ không thể push code mà bạn viết tiếp vào cục source đó được (có username, password của nó éo đâu). Vậy thì bạn cần phải đổi cái link repository của thằng đó sang link repository của bạn đúng không.</p>
<pre>git remote set-url origin &lt;link repository của bạn&gt;</pre>
<p>Đến bây giờ bạn <strong>git remote -v</strong> lại thì sẽ thấy remote link của cục source là của bạn chứ không còn là của thằng kia nữa. Giờ nó đã map với repository của bạn rồi nên cứ việc đẩy code lên git thôi.</p>
<h2>Branch (rẽ nhánh)</h2>
<p>Ở trên bộ ba pháp thuật, bạn thấy có khai báo <em>&lt;branch_name&gt;</em> khi push code lên đúng không. Mình sẽ không giải thích branch là gì, branch dùng làm gì vì nó đã được nói rất nhiều trên mạng rồi, hoặc bạn có thể xem <a href="https://guides.github.com/introduction/flow/" target="_blank" rel="noopener noreferrer">tại đây</a> để hiểu quy trình mà git làm việc. Branch mặc định của repository khi được tạo mới tên là <strong>master</strong>.</p>
<p>Để tạo mới 1 branch khác, mình dùng lệnh sau</p>
<pre>git branch &lt;tên branch&gt;</pre>
<p>Bạn có thể liệt kê danh sách branch hiện có bằng cách</p>
<pre>git branch</pre>
<p>Có nhiều branch quá, giờ muốn chuyển qua branch khác để code  mà không ảnh hưởng đến code hiện tại (trên branch master) thì làm sao đây. Chỉ cần dùng lệnh này để chuyển qua branch mới</p>
<pre>git checkout &lt;tên branch cần chuyển qua&gt;</pre>
<p>Nếu bạn chưa có branch cần chuyển, bạn cũng có thể vừa tạo vừa chuyển qua chỉ với 1 lệnh</p>
<pre>git checkout -b &lt;tên branch cần chuyển qua&gt;</pre>
<p>Ví dụ mình tạo branch mới tên là <strong>vietnam</strong> để phát triển link phim có nguồn gốc liên quan đến Việt Nam</p>
<pre>$ git branch vietnam    $ git checkout vietnam  Switched to branch 'vietnam'    </pre>
<p>Sau một thời gian cập nhật vào file text và push lên git miệt mài trên branch mới <strong>vietnam</strong>, bây giờ mình cần ghép (<strong>merge</strong>) code lại vào cây gốc (<strong>master</strong>). Trước tiên, cần phải checkout ra khỏi branch vietnam để vào branch master, sau đó thì dùng lệnh merge để ghép branch vietnam vào master</p>
<pre>$ git checkout master  $ git merge vietnam</pre>
<p>Sau khi merge xong thì đẩy lên branch <strong>master</strong> thôi, quá dễ phải không.</p>
<p>Thông thường khi merge hay xảy ra vấn đề conflict (nhất là khi làm dự án nhiều người) nên mấy bạn cần để ý kỹ. Giải quyết vấn đề conflict như thế nào, vì sao bị conflict là kỹ năng bạn cần tự tìm hiểu sau khi đã dùng git một thời gian, vì vậy mình sẽ không giải thích ở đây.</p>
<hr />
<p>Bây giờ, bạn đang có source trên máy nhưng source gốc của nó đã được người khác push dữ liệu mới lên. Và bạn muốn update lại source trên máy để nó giống với trên source gốc thì làm sao? Đầu tiên bạn phải chắc chắn source trên máy bạn chưa được chỉnh sửa gì kể từ lần cuối bạn push nó lên (vì nếu bạn sửa mà chưa push lên, bạn lại update trên remote repo xuống sẽ dễ gây conflict).</p>
<p>Wtf? Mình lỡ chỉnh sửa rồi thì sao? À thì <strong>git add</strong>, <strong>git commit</strong> nhưng đừng <strong>git push</strong>, sau đó dùng lệnh này</p>
<pre>git pull origin &lt;branch&gt;</pre>
<p>để kéo phần update mới về. Sẽ có 2 trường hợp xảy ra:</p>
<p>1. Phần code người khác up lên trước bạn không dính dáng tới file nào bạn đang sửa dưới local, hoặc dính nhưng không trùng với phần code bạn đang sửa ==&gt; May phước cho bạn là nó sẽ tự merge, bạn không cần làm gì.</p>
<p>2. Ngược lại với 1, sẽ có thông báo conflict xuất hiện và bạn phải fix bằng tay. Git đã hỗ trợ đánh dấu những phần bị conflict thành 2 bản (1 của người ta, 1 của bạn) nên sửa cũng khá dễ. Sau khi sửa và lưu lại thì bạn dùng lại bộ ba phép thuật git add, git commit và git push lại là thành công.</p>
<h2>Nâng cao một chút</h2>
<p>Sau một thời gian cập nhật link và commit file của bạn. Bây giờ bạn muốn xem lại lịch sử những lần commit đó thì làm sao? Lệnh git log sẽ cho bạn biết về người commit, ngày giờ, message của những lần commit đó.</p>
<pre>git log</pre>
<p>Ngoài ra, mỗi lần commit sẽ sinh ra một đoạn mã (hash) random ngoằn ngoèo giống như đoạn 69c7321d25334943a06796648d65c488c05c02c8. Đoạn hash này được coi như ID của lần commit đó, nó sẽ cho biết bạn thay đổi gì vào lần commit đó. Để xem được những thay đổi đó, dùng lệnh đơn giản sau</p>
<pre>$ git show &lt;đoạn hash&gt;</pre>
<p>Nếu một ngày đẹp trời bạn commit code và push lên remote repository, thật không may lần commit đó đã làm hỏng ứng dụng. Thay vì sửa lại dưới local và cứ để nguyên cái lỗi ở trên remote, sau khi sửa xong thì push cái mới lên, bạn lại muốn xóa bỏ dữ liệu của lần commit đó trên remote. Cách đơn giản nhất là bạn đưa HEAD của source về lại lần <strong>commit trước</strong> (trước <strong>commit muốn xóa</strong>), sau đó push code của lần <strong>commit trước </strong>lên, sau đó đưa HEAD quay về lại lần commit muốn xóa.</p>
<pre>$ git reset --hard HEAD@{1}    $ git push -f origin master    $ git reset --hard HEAD@{1}</pre>
<p>Chú ý: bạn cần phải chắc rằng không ai đang pull code lỗi của bạn hoặc đang cố gắng commit tiếp theo sau lần commit lỗi của bạn, vì bạn sẽ xóa nó. Đây là một việc làm khá nguy hiểm nên cần cân nhắc kỹ lưỡng trước khi thực hiện.</p>
<p>Đó là một số lệnh git cơ bản mình hay xài trong các dự án. Còn mấy lệnh nâng cao thì nhiều lắm, khi nào đụng thì mới research chứ không ai nhớ hết.</p>
<p>Các bạn có thể tham khảo thêm tại document của GIT: https://git-scm.com/docs</p>
</div>
</body>
</html>
