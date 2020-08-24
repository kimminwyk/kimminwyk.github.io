---
layout: post
title:  "FTZ download"
date:   2020-08-24 12:13
categories: blog
---

![ftz download](/blog_img/ftz_title.png)

+ 1. ftz 다운로드하기

__ftz 설치__
[hackerschool_ftz](https://drive.google.com/file/d/1krZs8e6QG_l_mxMI3eCY11F-lgb12HLb/view,"hackerschool_ftz")

__가상머신 다운로드(vmware player)__
[hackerschool_ftz](https://www.vmware.com/kr/products/workstation-player/workstation-player-evaluation.html,"vmware_download")

+ 2. ftz 로컬에 실행하기
	
ftz.zip 압축풀고 가상머신 적용하기 위해서 Vmware_Rdehat_9_FTZ.zip 를 압축 해제해준다.
![vmware_zip](/blog_img/zip.png)

vmware 및 가상머신을 설치에 완료했다면 실행을 한 다음  
![file_open](/blog_img/file_open.png)

원하는 가상머신에서 open a virtual machine 와 비슷한 텍스트를 클릭해서 Red Hat Linux.vmx 이라는 파일을 가져오고 실행을 하면은 
![it](/blog_img/vmware_it.png)

이 문구가 뜬다면은 I Copied It 이라는 버튼을 누르면은 된다.
이제 이 버튼을 누르고 막 화면에 쫘르르륵 나온다음
로그인을 해야되는 상황이 올것이다.
아이디:root
비밀번호:hackerschool
이렇게 입력을 하면은 된다. 근데 비밀번호 입력하는 부분에서 입력을 했는데도 안보이는 이유는 보안상의 이유로 비밀번호 입력이 안보이게된다. 이제 마지막으로 linux 에서 ifconfig 를 쳐서 아이피를 얻어야된다. 
![ifconfig](/blog_img/ftz_ifconfig.png)

위 사진에서 inet addr: 앞에있는 192. 뭐뭐뭐로 시작하는게 putty 에 입력해야될 ip 이다.
putty 라는 가상 단말이 프로그램을 깐다.
> [putty_download](https://putty.softonic.kr/)

putty 를 다운받은다음에 실행을 시킨다.
![putty_image](/blog_img/putty.png)

이렇게 실행을 완료했다면 host name 에 vmware 에서 ifconfig 를 입력하고 나온 아이피를 입력하고 port 에는 22 라고 입력을 한 다음 Open 을 누르면 된다.
이제 원하는 난이도로 로그인해서 하나씩 클리어하면은 된다. 

만약에 처음한다면 
id :level1
password:level1 를 입력해서 하나씩 클리어해나가면된다.



