# AutoBuild-OpenWrt

Build OpenWrt firware [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) using GitHub Actions  
Hereby thank P3TERX for his amazing job: https://github.com/P3TERX/Actions-OpenWrt/

## Usage

- Sign up for [GitHub Actions](https://github.com/features/actions/signup)
- Fork [this GitHub repository](https://github.com/esirplayground/AutoBuild-OpenWrt)
- Click [.github/workflows] folder on the top of repo and you could see two workflow files, one's for x86 32bit and the other's for x86_64.
- Edit the workflow file you desire，uncomment push section 3 lines together and submit the commit.(Other 2 methods wait you to discover)
- The build starts automatically. Progress can be viewed on the Actions page.
- When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.

[For the details please visit my Y2B Channel (in Chinese) | 视频教程](https://www.youtube.com/c/esirplayground)

配置项说明（在线excel） ： https://onedrive.live.com/view.aspx?resid=64C9D95F1BBD0FAF!16042&ithint=file%2cxlsx&authkey=!AKR-UGHOsqhY1cc

配置项引用：
https://www.right.com.cn/forum/thread-1237348-1-1.html
https://www.right.com.cn/forum/thread-344825-1-1.html

##### 不要fork 不要fork 不要fork 
##### 里面内容是按照我自己的需求修改的，不一定适合你.

-------
主要修改了`x86_64`的配置 
1. 取消固件压缩，因为`github` `actions/upload-artifact`本身会压缩，它不支持直接上传文件 [issue](https://github.com/actions/upload-artifact/issues/3) . 
2. 分区调整为`512M 2G` (原来是`64M 300M`)
3. 增加一套主题，增加`Vim`和`screen`
4. 取消虚拟机VMDK文件的生成,(我物理机直接装，用不上)
5. 拆分构建成功后打包文件:
    `OpenWrt packages`: 这次构建中所有的`ipk`插件
    `OpenWrt firmware(combined+uefi)`：构建后的整个`targets`文件夹，包含`combined+uefi`
    `OpenWrt firmware(combined)`： 只有`combined`的`img`固件
    `OpenWrt firmware(uefi)`： 只有`uefi`的`img`固件