# LOINC-FORM-VN
LOINC-FORM
Informational Notice: 

This software, LForms, was developed by the National Library of Medicine (NLM) Lister Hill National Center for Biomedical Communications (LHNCBC), part of the National Institutes of Health (NIH).

Please cite as: http://lhncbc.nlm.nih.gov/project/lforms

This software is distributed under the license set forth below, which is based on the BSD open-source license.  

No warranty or indemnification for damages resulting from claims brought by third parties whose proprietary rights may be infringed by your usage of this software are provided by any of the owners.


LICENSE

Owner Notice: The Owner of this software, LForms, is the National Institutes of Health/Department of Health and Human Services, Bethesda, MD, U.S.A.
All rights reserved.

The software includes elements owned by Joyent, Inc., TJ Holowaychuk, Google, Inc., Kit Cambridge, Kristopher Michael Kowal, jQuery Foundation, Twitter, Inc, The AngularUI Team, and Karsten Sperling, who have distributed them to NIH under the MIT open-source license.  

Redistribution and use in source and binary forms, with or without modification, are permitted for commercial and non-commercial purposes and products alike, provided that the following conditions are met:

  * Redistributions of source code shall retain the above Owner Notice, this list of conditions and the following disclaimer.
  * Redistributions in binary form shall reproduce the above Owner Notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
  * Neither the names of the National Library of Medicine (NLM), the Lister Hill National Center for Biomedical Communications (LHNCBC), the National Institutes of Health (NIH), nor the names of any of the software contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE OWNER AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,  EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
# RUN LOINC UNBUTU
-	Tải và cài đặt VMWare workstation
-	Tải bộ cài Ubuntu trên trang chủ và cài đặt lên VMWare (hoặc có thể cài song song cùng với windows)
-	Yêu cầu tối thiểu 20 GB ổ cứng và 4 GB RAM
-	Cài đặt môi trường dựa vào các thông tin sau trong file readme.md
          * Install Node.js (version 14 is what we are currently using, but it should work with later versions)
            Clone the lforms repository and cd to its directory
          * source bashrc.lforms   # (make sure node dir is available at ~/)
          * npm ci
          * source bashrc.lforms # to add node_modules/.bin to your path
          * npm run build # build both FHIR libs and LHC-Forms web component
          * npm run start # starts the app we use for testing
          * npm run test # runs the unit tests and e2e tests

      +	Git 
      +	nodejs version 18 (bắt buộc vì angular CLI đã được cập nhật và yêu cầu tối thiểu phiên bản nodejs 18)
      + npm phiên bản mới nhất cũng được
      +	***sua lại package build:version: ""build:version": "node -e \"require('fs').writeFileSync('src/version.json', JSON.stringify({lformsVersion: require('./package.json').version}))\"","
      +	Xóa thư mục dist, node_modules, package-lock.json
      +	project cần build lần đầu trước khi chạy, build lần đâu bằng lệnh "npm run build"
      + chạy project bằng lệnh "npm run start"

-	Tăng giới hạn watchers trên ubuntu bằng cách sau:
Mở terminal và chạy những lệnh sau:
cat /proc/sys/fs/inotify/max_user_watches (xem giới hạn watchers hiện tại)
sudo sysctl fs.inotify.max_user_watches=524288 (set số lượng watchers mới)
sudo nano /etc/sysctl.conf (mở file sysctl.conf)
fs.inotify.max_user_watches=524288 (dán thêm dòng lệnh này, sau đó ấn Ctrl O => enter để lưu, Ctrl X để thoát text editor)
sudo sysctl -p (áp dụng cấu hình mà không cần khởi động lại máy)
-	Chạy dự án thành công sau khi thực hiện các bước trên
-	Sau khi truy cập localhost:4200 sẽ tự redirect sang Test page

