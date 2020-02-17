# 工作记录

## 目录
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [工作记录](#工作记录)
  - [目录](#目录)
  - [记录](#记录)
    - [20200217](#20200217)
      - [打包发布](#打包发布)
      - [尝试上云](#尝试上云)
      - [下一步工作](#下一步工作)

<!-- /code_chunk_output -->

## 记录

### 20200217

#### 打包发布

1. 在工程中的 `app_id.txt` 中更改 `appid`
2. 同时将文件夹`com.example.demo`的名称改为设置的 `appid`
3. 在coolq中进行打包
4. 在文件夹中可找到对应 cpk 文件

#### 尝试上云

1. 阿里云服务器租用
    * ￥9.5/month
    * Ubuntu 18.04

2. 主要原理
    * coolq 原生 windows 平台运行
    * 在 Ubuntu 中使用 Docker 容器运行 coolq
        * [Docker](https://yeasy.gitbooks.io/docker_practice/content/) 是一个 `容器`
        * docker.io 版本比较老
        * docker-ce 为最新安装方式

3. 在服务器中部署 ftp 以方便文件管理
    * 服务器端使用 [vsFTPd](https://www.jianshu.com/p/c8947a59c96a)
    * 本地使用 FileZilla

4. coolq 在 Docker中可以运行，但原生 “爱音乐” app不可正常运行，所有上传的 .cpk 文件无法正常加载
    * docker.io 与 docker-ce 均无法正常运行
![](./images/error1.png)

#### 下一步工作

1. 与nxp交流，得知 [包含httpAPI的docker](https://github.com/richardchien/cqhttp-docker) 不报错，可以进行尝试

2. 考虑 [httpAPI 插件的 Docker](https://cqhttp.cc/docs/4.14/#/Docker) 适配问题
    * 确认是否是少了什么适配
    * 怀疑问题所在：

    >注意如果 酷Q 启动时报错说插件加载失败，或者系统弹窗提示缺少 DLL 文件，则需要安装 Visual C++ 可再发行软件包（点击链接即可从官方下载，如果自行安装，一定要装 x86 也就是 32 位版本！），如果你的系统是 Windows 7 或 Windows Server 2008、或者安装 Visual C++ 可再发行软件包之后仍然加载失败，则还需要安装 通用 C 运行库更新，在这个链接里选择你系统对应的版本下载安装即可。如果此时还加载失败，请尝试重启系统。
    
    * [来源](https://cqhttp.cc/docs/4.14/#/?id=%E6%89%8B%E5%8A%A8%E5%AE%89%E8%A3%85)

3. 完成“定时响应”功能
    * 确认当前时间
    * 存储事件时间