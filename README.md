# linux-user-check
检查linux用户登录时间及登录IP以及是否被增加用户  
  
前端时间有玩家问怎么检查云主机的用户登录情况及检查是否有被偷偷增加了用户,因为玩家怕主机帐号被入侵了,我这个小小白只好研究一下了 ( ´•︵•` )   
  
找了网上一堆的大神命令,列出来的都是一堆复杂的用户数据表,最简单的也是所有用户名字的列表,但仔细研究一下发现所有用户列表包括了绝大多数的系统内建用户名字,这样对于玩家提出的检查用户的要求是不符合的,因为玩家只需要列出root用户及普通用户,而系统内建用户他不关心,如果按那些大神的命令扔给玩家,他不得砍我呀 °.°·(((p(≧□≦)q)))·°.°   
  
于是再研究研究,终于研究出下面几键了 ₍₍٩( ᐛ )۶₎₎♪   
  
查系统的root用户及所有普通用户名字   
转用root用户  
$su  
  
列出root及其他所有普通用户   
#getent passwd | grep '/bash' | cut -d: -f1    
结果只会输出root用户及非系统内建的普通用户名字,这样玩家就可以看到是否有偷偷增加的普通用户了,因为对玩家来说,一个自己的主机建了多少用户自己是有点13数的    
   
当然玩家有兴趣就可以列出所有用户数据看看    
#getent passwd   
   
也可以只列出所有用户的名字   
#getent passwd | cut -d: -f1     
   
列完用户名字,就可以查用户的登录时间了,有两个列的方法   
   
按用户名列出最后登录时间   
#lslogins -u   
    
查所有登录用户的曾经登录时间及登录使用的IP地址    
#last     
  
查当前登录用户信息及登录使用的IP地址  
  
#w  
  
