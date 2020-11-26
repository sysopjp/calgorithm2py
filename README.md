
# 使い分けメモ

 
`ssh-keygen -t rsa -C [登録メアド] -f id_rsa_op`
`ssh-keygen -t rsa -C [登録メアド] -f id_rsa_jp`


vi ~/.ssh/config

```
Host github.com.sys # メインアカウント
  HostName github.com
  User git
  Port 22
  IdentityFile ~/.ssh/id_rsa 
  TCPKeepAlive yes
  IdentitiesOnly yes

Host github.com.op # サブアカウント1
  HostName github.com
  User git
  Port 22
  IdentityFile ~/.ssh/id_rsa_op
  TCPKeepAlive yes
  IdentitiesOnly yes

Host github.com.jp # サブアカウント2
  HostName github.com
  User git
  Port 22
  IdentityFile ~/.ssh/id_rsa_jp
  TCPKeepAlive yes
  IdentitiesOnly yes
```

`ssh -T git@github.com.sys`
`ssh -T git@github.com.op`
`ssh -T git@github.com.jp`

##  リポジトリで
```
git --local user.name  sysopjp
git --local user.email xxxxxx@yyyy.com
git remote add origin git@github.com:sysopjp/calgorithm2py.git
git add .
git commit -m '1st commit'
git push --set-upstream origin master
```
