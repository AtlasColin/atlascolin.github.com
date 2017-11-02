#多个rsa的切换

ssh的config文件该文件位置为`$home/.ssh/config`。内容如下：

```
Host github.com  
    HostName github.com  
    PreferredAuthentications publickey  
    IdentityFile ~/.ssh/id_rsa  
  
Host atlascolin.github.com  
    HostName github.com  
    PreferredAuthentications publickey  
    IdentityFile ~/.ssh/id_rsa_atlas  
```

不难看出，其格式为

```
Host USER_HOST     ;USER_HOST为自定义host名字，如上面的personal和company
HostName SERVER_HOST   ;SERVER_HOST为实际服务器host，此时为GitHub
PreferredAuthentications publickey 
IdentityFile PRIVATE_KEY      ;PRIVATE_KEY为本地key
```

当再次clone一个新Repos时，如果其ssh地址为`git@github.com:atlas/xxx.git`，使用`git clone git@atlascolin.github.com:atlas/xxx.git`即可clone到本地（**注意github.com换成了自定义的atlascolin.github.com**），并且push时也不用输入任何验证。