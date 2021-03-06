项目名称: 基于Qt+mysql的联机斗地主  

  
服务端特点:  
{  
    独立的注册服务与游戏服务  
    {  
       两个服务可以分开部署,互不影响  
    }  
    避免多余连接,限制长连接  
    {  
       注册时不论成败,服务端都主动断开连接(因为注册后不一定马上进入游戏)  
       游戏服务器端只保留登陆成功的玩家的套接字  
       游戏服务端有在线人数限制  
    }  
    准确丰富的牌型  
    {  
       加入了以A开头的顺子和连对  
       加入了以2开头的顺子和连对  
    }  
    能处理玩家断线  
    {  
       若未开始游戏,同一房间的其他玩家会看到那个玩家的头像消失了  
       若已开始游戏,则敌对势力获胜  
    }  
    出牌时间限制  
    服务端监视界面提供了类似于"命令行"的详细的日志输出  
}  
  
  ------------------------------------------------------------  
  
客户端特点:  
{  
    有效处理快速连续点击按钮所导致的异常情况  
    出牌时间限制  
    提供了游戏时的匿名聊天功能  
    提供了一键安装包( 针对windows的安装包 )  
    提供了单击AI(带有各种音效和智能提示)  
}  
  
  ------------------------------------------------------------  
  
配置文件config.txt解说  
//若当前编译是debug模式,则该文件位于Maingame-debug目录下  
//若当前编译是release模式,则该文件位于Maingame-release目录下  
//若是要执行安装后的快捷方式,则该文件位于安装的根目录下  
修改对应模式下的config.txt:  
{  
    第一行代表 游戏服务器的地址  
    第二行代表 注册服务器的地址  
    第三行代表 游戏服务器端的端口号(此项一般不变)  
    第四行代表 注册服务器端的端口号(此项一般不变)  
}  
  
  ------------------------------------------------------------  
  
数据库要求  
驱动: mysql  
用户名: root  
密码: 空  
数据库名称: doudizhu  
数据表名称: usertable  
字段名        含义        类型            格式要求  
username      用户名      char(8)         [0-9]{2}[0-9a-zA-Z]{1}14[0-9]{3}  
password      密码        char(9)         21314[0-9]{4}  
totaltimes    游戏局数    unsigned int    无  
wintimes      胜利局数    unsigned int    无  
head          头像代号    int             属于[0,2]  