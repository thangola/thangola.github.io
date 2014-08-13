---
layout: post
title: "1 vài ví dụ sử dụng awk phần 1"
date: 2014-08-13 13:01:28 +0700
comments: true
categories: shell awk
---

AWK là ngôn ngữ lập trình được nhằm mục đích xử lý các Tập tin chữ (text file) theo nguyên lý khớp mẫu (pattern matching); đồng thời còn là tên gọi một chương trình trong hệ điều hành UNIX. Trong UNIX các chương trình được viết tên chữ thường nên AWK còn được gọi là Awk hoặc awk.
Sử dụng awk thì chắc nói cả ngày cũng không hết được nên hôm nay mình sẽ đưa ra 1 vài ví dụ hay dùng đến awk và cực kỳ đơn giản, dễ hiểu (mooning).

**Ví dụ 1:** In cột trong file <br/>
Bạn muốn in cột thứ 3 của tất cả các dòng trong 1 file: <br/>

`awk '{ print $3 }' file`

**awk sẽ tự động cắt các cột của từng dòng đưa vào biến $1, $2, $3...$n**<br />


** Ví dụ 2:** In ra toàn bộ dòng trong 1 file theo số thứ tự <br />


`awk '{ print NR ": " $0 }' file`



** NR là 1 biến đặc biệt, nó chứa số thứ tự của dòng in ra** <br />


** Ví dụ 3: ** In ra số từ trong 1 file <br />



`awk '{ total = total + NF } END { print total }'`



** NF: 'number of fields, or number of columns, or number of words' **  <br />


** Ví dụ 4: ** In ra những dòng nào chứa ít hơn n ký tự: <br />



`awk 'length < 64' `




** Ví dụ 5: ** In ra n dòng đầu tiên của file (tương đương head -n ) <br />

`awk 'NR < n'`

** sau khi đọc xong mỗi dòng, awk sẽ tự động tăng lên 1 giá trị** <br />


** Ví dụ 6: ** In ra các dòng trong khoảng : n < line < m <br />

`awk 'NR==n,NR==m'`

** Ví dụ 7: ** In ra dòng thứ n trong file <br />

`awk 'NR==n'`
<br />

** Ví dụ 8: ** Xoá toàn bộ các dòng trống (blank line ) trong file <br />
`awk NF`



** Trong phần sau mình sẽ đưa ra các ví dụ về ghi trong awk **
