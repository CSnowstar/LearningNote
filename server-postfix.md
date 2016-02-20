# postfix 向 gmail 发送邮件

实验环境 RHEL7.1

### 1.  设置默认邮件服务
Linux 可以同时存在多个 sendmail 程式，通常是 sendmail, postfix 等，RHEL6 以上的版本默认装的是 postfix

* 由于我用的是 RHEL7.1, 默认没有装 sendmail，为了体验一下设置默认邮件的快感，我决定装一个玩玩:

    `yum install -y sendmail`

* 嗯, 装好了, 看看发生了什么:

    ```
    [root@snowstarcyan ~]# alternatives --config mta

    共有 2 个提供“mta”的程序。

      选项    命令
    -----------------------------------------------
       1           /usr/sbin/sendmail.postfix
    *+ 2           /usr/sbin/sendmail.sendmail

    按 Enter 保留当前选项[+]，或者键入选项编号：1
    ```

* 把 postfix 切为默认

    ```
    [root@snowstarcyan ~]# alternatives --config mta

    共有 2 个提供“mta”的程序。

      选项    命令
    -----------------------------------------------
     + 1           /usr/sbin/sendmail.postfix
    *  2           /usr/sbin/sendmail.sendmail

    按 Enter 保留当前选项[+]，或者键入选项编号：1
    ```

* **疑问:**

    2. 这里 sendmail 的 * 是啥意思?

### 2. 发送邮件给自己的邮箱
    - 输入 `mail -s "title" 997596@gmail.com` 回车
    - 输入邮件内容
    - 按 Ctrl+D 结束并发送
    - 大概20多秒后, 在gmail的垃圾邮件箱里翻出了这封邮件。
        - _Tips: 这里是因为IP和域名不符合而进入垃圾邮件_

### 3. 发送邮件给本机
    - 输入 `mail -s "title" localhost` 回车
    - 输入邮件内容
    - 按 Ctrl+D 结束并发送
    - 使用 mutt 命令查看收到的邮件
        - _Tips: 若没有这条命令则安装 `yum -y install mutt`_
    - 然后发现了很多系统发的邮件, 和刚刚发那封放在一堆


### 4. 测试邮件别名
    先清空本机邮件
    `...待续`
