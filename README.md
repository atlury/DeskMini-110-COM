因为自己用deskmini，就动手改了7.2版的bios（支持Cfl i3处理器Revision B0和核显），已刷机测试可以正常使用等。

注意：不能直接更新官方新版的BIOS，因为会更新ME等导致不能开机！

百度网盘分享https://pan.baidu.com/s/1c2JHlc8 ，如有风险请自行承担！

大众教程：下载修改好的BIOS "H11STXC7.80np+me116+vbios1059+gop1080.7z"，解压缩放到U盘（FAT32格式），接着重启进BIOS查看BIOS版本：

    7.20或以下版本直接用instant flash刷带np（去除安全校验）的ROM即可；
    7.30或更高版本的，请按“wiki--04 ME unlock降级”解锁ME，再用instant flash刷带np（去除安全校验）的ROM。
    
请用同一批次的品牌内存条组双通道，我用的是JD买的金士顿骇客神条（1号机）和天猫买的Apacer（2号机），核显驱动用Win10自动更新安装的；
至今还未遇到死机或花屏等问题！此外不要用Win7系统，因为没有对应的8代核显驱动等。


进阶教程，操作流程简述：

    A）下载官方的7.20版BIOS，记得区分DeskMini 110 (H110M-STX)和DeskMini 110/COM (H110M-STX/COM)；
       国行是COM版，基本上BIOS芯片都是焊在主板上的，要用编程器（推荐SkyGz）的可以买编程器夹子（宽体），
       用编程器就不需要6代或7代亮机U了。
    
    B）用MMTool_5.02.0024修改处理器微码，详细见“wiki--02 修改处理器微码”，添加对CFL处理器的支持

    C）按“wiki--03 合成新版VBIOS”来生成1054版的VBIOS，另存为vbios1054.bin

    D）用UEFITool_0.22.1打开H11STXC7.20mod.rom，
       Ctrl+F搜索GUID{380B6B4F-1454-41F2-A6D3-61D1333E8CB4}即GOP模块，找到后选中，
       右键Replace body…选择Intel_Skl-Kbl-Cfl_GopDriver_v9.0.1074.bin（网盘里有分享）替换；
       接着Ctrl+F搜索GUID{C5A4306E-E247-4ECD-A9D8-5B1985D3DCDA}即VBIOS模块，
       找到后选中，右键Replace body…选择刚才的vbios1054.bin替换，保存H11STXC7.20mod.rom
   
       至此完成H110主板对Cfl处理器的识别、核显支持的BIOS修改操作。
       
    E）可选；7.20或以下版本BIOS的请跳过该步。
       如果你的bios是7.30版则需要解锁ME，该版的ME是v11.8.50.3425不支持在100系主板上用CFL处理器，
       识别CFL后ME会让主板自动断电关机；而7.20版BIOS的ME固件是v11.6.0.1126就不会有这样的问题。
       解锁ME教程请跳转“wiki--04 ME unlock降级”。
       
       想继续用7.30版BIOS的，可以提取7.20版BIOS的ME替换到该版BIOS，按上面步骤生成7.30的修改版BIOS。

    F）最后用AFUWIN刷修改好的BIOS，AFUWIN里不要选自动重启、万一操作出错还能补救。
       想用instant flash更新BIOS的，请用UBU工具去除安全校验：将BIOS ROM放到UBU目录下、运行UBU.bat即可。
       非华擎主板碰到AFU不能刷的，可以尝试用Intel Flash Programming Tool（网盘里有分享），
       强烈建议先用FPT备份好BIOS ROM再操作。
       
   2018-6-23 Remark：华擎天猫店开卖DeskMini 310/COM了，目前价格￥1299还是稍贵。
   
   2018-9-17 DeskMini 110/COM基于最新的7.80版修改，已刷机测试。    
       
