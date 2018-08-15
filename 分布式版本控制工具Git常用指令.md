## 分布式版本控制工具Git常用指令

- git  config   --global user.name "自定义名字"

- git  config  --global user.email  "@邮箱地址"

- git  init                        //通过命令把这个目录变成Git可以管理的仓库

- touch   .gitignore     //在工程目录下生成忽略文件，可编写忽略文件https://github.com/github/gitignore忽略写法

- git  status                                                  //获取当前更新，以及当前提交状态

- git   add    --all或git   add   .                   //提交当前项目下的所有文件到本地服务器    

- git  commit   -m   “自定义日志内容”     //提交指令

- git   log                                                    //获取提交日志

- git   reflog                                              //获取每次提交日志   

- git  log   -n（次数）                              //获取指定次数提交日志

  ## 回退指令

- git   reset   --hard     HEAD^                   //回退到上一次修改版本

- git   reset   --hard     HEAD~n(次数)      //回退到指定次数版本

- git   reset   --hard   commit   id            //回退到指定ID版本

  ## 分支指令

- git   checkout   -b   分支名                  //创建一个分支并命名 

- git   branch  -d   分支名                      //删除指定名字的分支   

- git  checkout   master                       //切换到主分支

- git   checkout   分支名                       //切换到指定分支

- git   branch                                        //获取当前所在状态

  ## 分支合并指令

- git   merge   分支名                          //需切换到主分支再进行合并

  ## 远程仓库GitHub

- ssh-keygen  -t  rsa  -C "邮箱地址"           //创建SSH KEY

- git  remote                                                //查看是否与远程仓库相关联

- git   remote    add   origin 加关联地址   //与远程仓库相关联

- git   push   -u  origin  master                  //把本地服务器的内容推送到远程仓库 

  

  

  

  

 





