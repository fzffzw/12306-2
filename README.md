### 12306

- python版本支持
  - 2.7
- 依赖库
  - 依赖打码兔 需要去打码兔注册账号，打码兔账号地址：http://www.dama2.com，一般充值1元就够用了
  - 项目依赖包 requirements.txt
  - 安装方法 pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -r requirements.txt

- 项目开始
  - 修改config/ticket_config.yaml文件，按照提示更改自己想要的信息
  - 运行根目录run.py，即可开始

- 目录对应说明
  - agency - cdn代理
  - config - 项目配置
  - damatuCode - 打码兔接口
  - init - 项目主运行目录
  - myException - 异常
  - myUrllib - urllib库

- 思路图
     ![image](https://github.com/testerSunshine/12306/blob/master/uml/uml.png)

- 项目声明：
  - 本软件只供学习交流使用，务作为商业用途，交流群：286271084
  - 能为你抢到一张回家的票，是我最大的心愿

- 成功log，如果是购票失败的，请带上失败的log给我，我尽力帮你挑，也可加群一起交流，程序只是加速买票的过程，并不一定能买到票
    ```
    正在第355次查询  乘车日期: 2018-02-12  车次G4741,G2365,G1371,G1377,G1329 查询无票  代理设置 无  总耗时429ms
    车次: G4741 始发车站: 上海 终点站: 邵阳 二等座:有
    正在尝试提交订票...
    尝试提交订单...
    出票成功
    排队成功, 当前余票还剩余: 359 张
    正在使用自动识别验证码功能
    验证码通过,正在提交订单
    提交订单成功！
    排队等待时间预计还剩 -12 ms
    排队等待时间预计还剩 -6 ms
    排队等待时间预计还剩 -7 ms
    排队等待时间预计还剩 -4 ms
    排队等待时间预计还剩 -4 ms
    恭喜您订票成功，订单号为：EB52743573, 请立即打开浏览器登录12306，访问‘未完成订单’，在30分钟内完成支付！
    ```

- 2017.5.13跟新
    - 增加登陆错误判断（密码错误&ip校验）
    - 修改queryOrderWaitTime，校验orderId字段bug，校验msg字段bug，校验messagesbug
    - 修改checkQueueOrder  校验 data 字段的列表推导式bug
    - 增加代理ip方法，目前已可以过滤有用ip


- 2018.1.7 号更新
    - 增加自动配置
        ```
        #station_date:出发日期，格式ex：2018-01-06
        #from_station: 始发站
        #to_station: 到达站
        #set_type: 坐席(商务座,二等座,特等座,软卧,硬卧,硬座,无座)
        #is_more_ticket:余票不足是否自动提交
        #select_refresh_interval:刷新间隔时间，1为一秒，0.1为100毫秒，以此类推
        #ticke_peoples: 乘客
        #damatu：打码图账号，用于自动登录
        ```
    - 优化订票流程
    - 支持自动刷票，自动订票

- 2018.1.8 更新
    - 增加小黑屋功能
    - 修复bug若干
    - 增加多账号同时订票功能
    -  增加按照选定车次筛选购买车次

- 2018.1.9 更新

    - 增加手动打码，只是登录接口，完全不用担心提交票的效率问题，要挂linux系统的话，还是去注册个打码兔吧
    ```
    思路
    1.调用PIL显示图片
    2.图片位置说明，验证码图片中每个图片代表一个下标，依次类推，1，2，3，4，5，6，7，8
    3.控制台输入对应下标，按照英文逗号分开，即可手动完成打码，
    ```
    - 修改无座和硬座的座位号提交是个字符串的问题
    - 增加校验下单需要验证码功能
    - 增强下单成功判断接口校验

- 2018.1.10 更新
    - 优化查票流程
    - 修改二等座的余票数返回为字符串的问题
    - 优化订单查询bug
- 2018.1.12更新
    - 优化抢票页面逻辑
    -增强代码稳定性

- 2018.1.13更新
    - 修改下单验证码功能
    - 优化大量调用user接口导致联系人不能用，理论加快订票速度
    - 增加邮箱功能
    ```
    #is_email: 是否需要邮件通知 ex: True or False 切记，邮箱加完一定要到config目录下测试emailConf功能是否正常
    #email: 发送的邮箱地址 ex: 1@qq.com
    #notice_email_list: 被通知人邮箱 ex: 2@qq.com
    #username: 邮箱账号
    #password: 邮箱密码
    #host: 邮箱地址
    ```

- 2018.1.14更新
    - 优化订票流程
    - 优化挂机功能
        - 修改之前程序到11点自动跳出功能，现在修改为到早上7点自动开启刷票
        - 需要开启打码兔代码功能，is_aotu_code 设置为True
    - 增加异常判断


