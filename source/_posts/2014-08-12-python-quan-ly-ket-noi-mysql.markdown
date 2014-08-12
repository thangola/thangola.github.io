---
layout: post
title: "Python: quản lý kết nối MySQL"
date: 2014-08-12 14:08:37 +0700
comments: true
categories: python
author: Kao Tac Nhan
---


Khi sử dụng Python để code 1 vài tool hay script với Mysql,tornado.... mình hay gặp lỗi "Dealing with OperationalError 2006, 'MySQL server has gone away". Cái này do kết nối giữa mysql
và python bị timeout, lúc gọi lại hàm thì nó chưa được reconnect.Dưới đây là đoạn code đơn giản để bạn **avoid** chuyện đấy:

<pre><code>
import MySQLdb

class DB:
  conn = None

  def connect(self):
    self.conn = MySQLdb.connect()

  def query(self, sql):
    try:
      cursor = self.conn.cursor()
      cursor.execute(sql)
    except (AttributeError, MySQLdb.OperationalError):
      self.connect()
      cursor = self.conn.cursor()
      cursor.execute(sql)
    return cursor

db = DB()
sql = "SELECT * FROM foo"
cur = db.query(sql)
# wait a long time for the Mysql connection to timeout
cur = db.query(sql)
# still works

</code></pre>
