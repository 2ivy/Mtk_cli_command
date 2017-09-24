
本文列举的当前会遇到的所有cli命令（截止到2017-09-22），后续有更新请提示我，我会更新
=======

准备工作
=====
使用 `su` 或者 `su7411` 命令开启权限(**千万不能重复使用，会导致无法开启su权限**)，然后输入 `cli` 进入cli命令界面，再次输入 `b.scm 0 mtkcli` 获取最高权限。
出现如下的提示说明你权限获取正确了~

    DTV>b.scm 0 mtkcli
    Set system cli mode : 0

根目录页
=====
|命令|简要解释|
|:------|:--------------------|
|[cd](#cd)                     |Change current directory
|[do](#do)                     |Repeat command
|[alias(a)](#alias)               |Add/Show current alias
|[ls](#ls)                   |Recursive list all commands
|[read(r)](#read)                |Memory read(word)
|[write(w)](#writer)                 |Memory write(word)
|[customer(cust)](#customer)           |Get customer name
|[basic_(b)](#basic_)                |basic command
|[linuxmode(l)](#linuxmode)             |Turn on/off linux mode
|[mtktool(0)](#mtktool)               |mtktool command
|[osd](#osd)                      |Osd driver
|[pmx](#pmx)                     |pmx command
|[sif](#sif)                      |Sif command
|[pwm](#pwm)                      |Pwm command
|[eeprom](#eeprom)                   |Eeprom command
|[nim](#nim)                      |Nim command
|[ir](#ir)                       |Ir command
|[rtc(rtc)](#rct)                 |RTC commands
|[aud](#aud)                      |Aud command
|[nptv(n)](#nptv)                  |Nptv command
|[av](#av)                     |Audio/Video command
|[vdp](#vdp)                      |Video plane command
|[prescale](#prescale)                 |Prescale cmd
|[fbm](#fbm)                      |Frame buffer manager command
|[dbs](#dbs)                      |Dbs command
|[mpv](#mpv)                    |MPEG Video Decoder command
|[vdec](#vdec)                   |Vdec command
|[tcon](#tcon)                     |Tcon command
|[ptp](#ptp)                      |PTP control command
|[muxer(mx)](#muxer)              |MUXER command
|[dmx(d)](#dmx)                   |Demux commands
|[memtest](#memtest)                  |Memory test
|[cec](#cec)                      |HDMI CEC test
|[cbus](#cbus)                     |HDMI CBUS test
|[pdwnc(pdwnc)](#pdwnc)             |PDWNC commands
|[jpg](#jpg)                    |Jpeg command
|[gpio](#gpio)                     |Gpio interface
|[mid](#mid)                    |Memory intrusion detection
|[swdmx](#swdmx)                  |SWDMX command
|[feeder](#feedr)                 |FEEDER command
|[tve](#tve)                      |Tve command
|[timeprofile](#timeprofile)              |timeprofile test
|[bim](#bim)                      |BIM module test
|[pcmcia(p)](#pcmcia)                |Pcmcia command
|[os](#os)                     |OS command
|[linux](#linux)                  |Linux commands
|[gfx](#gfx)                    |Gfx command
|[imgrz](#imgrz)                  |Imgrz command


第一级别命令用法解释
=====
<h4 id="cd">cd</h4>

`cd` 命令用来打开每一层级的功能列表，可以看做是打开文件夹。
<h4 id="do">do</h4>

`do` 命令用来再次输入前一次的命令。
<h4 id="alias">alias(a)</h4>

`alias` 用于对你常用的命令取别名。一般不常用，因为这个别名存储在本地设备，我们一般调试完一台机器就完了，频次不高，没有设置别名的需求。**可以使用括号中的简写代替本条命令~**
<h4 id="ls">ls</h4>

`ls` 命令用来列出本页所有可用命令，直接按 `Enter` 也是一样的效果。
<h4 id="read">read(r)</h4>

`read` 命令
<h4 id="write">write(w)</h4>

`write` 命令
<h4 id="customer">customer(cust)</h4>

`customer` 用于获取客户名称
<h4 id="basic_">basic_(b)</h4>

`basic_` 命令
<h4 id="linuxmode">linuxmode(l)</h4>

`linuxmode` 命令
<h4 id="mtktool">mtktool(0)</h4>

`mtktool` 命令
<h4 id="osd">osd</h4>

`osd` 命令
<h4 id="pmx">pmx</h4>

`pmx` 命令用来修改屏参，PQ相关的参数。[详见](#pmx2)
<h4 id="sif">sif</h4>

`sif` 命令
<h4 id="pwm">pwm</h4>

`pwm` 命令
<h4 id="eeprom">eeprom</h4>

`eeprom` 命令
<h4 id="nim">nim</h4>

`nim` 命令
<h4 id="ir">ir</h4>

`ir` 命令
<h4 id="rtc">rtc(rtc)</h4>

`rtc` 命令
<h4 id="aud">aud</h4>

`aud` 命令
<h4 id="nptv">nptv(n)</h4>

`nptv` 命令
<h4 id="av">av</h4>

`av` 命令
<h4 id="vdp">vdp</h4>

`vdp` 命令
<h4 id="prescale">prescale</h4>

`prescale` 命令
<h4 id="fbm">fbm</h4>

`fbm` 命令
<h4 id="dbs">dbs</h4>

`dbs` 命令
<h4 id="mpv">mpv</h4>

`mpv` 命令
<h4 id="vdec">vdec</h4>

`vdec` 命令
<h4 id="tcon">tcon</h4>

`tcon` 命令
<h4 id="ptp">ptp</h4>

`ptp` 命令
<h4 id="muxer">muxer(mx)</h4>

`muxer` 命令
<h4 id="dmx">dmx(d)</h4>

`dmx` 命令
<h4 id="memtest">memtest</h4>

`memtest` 命令
<h4 id="cec">cec</h4>

`cec` 命令
<h4 id="cbus">cbus</h4>

`cbus` 命令
<h4 id="pdwnc">pdwnc(pdwnc)</h4>

`pdwnc` 命令
<h4 id="jpg">jpg</h4>

`jpg` 命令
<h4 id="gpio">gpio</h4>

`gpio` 命令
<h4 id="swdmx">swdmx</h4>

`swdmx` 命令
<h4 id="feeder">feeder</h4>

`feeder` 命令
<h4 id="tve">tve</h4>

`tve` 命令
<h4 id="timeprofile">timeprofile</h4>

`timeprofile` 命令可以开启timeprofit测试
<h4 id="bim">bim</h4>

`bim` 命令可以开启BIM模式测试
<h4 id="pcmcia">pcmcia(p)</h4>

`pcmcia` 命令页
<h4 id="os">os</h4>

进入`os` 命令页
<h4 id="linux">linux</h4>

进入`linux` 命令页
<h4 id="gfx">gfx</h4>

进入`gfx` 命令页
<h4 id="imgrz">imgrz</h4>

进入`imgrz` 命令页

---
---

第二级别命令用法解释
=====
<h3 id="pmx2">DTV.pmx</h3>

|命令|命令解释|
|:---------|:----------|
|[init(i)](#init)                |init
|[enable(e)](#enable)              |enable/disable LVDS
|[pattern(p)](#pattern)             |enable/disable test pattern
|[pat chg(pc)](#pac_chg)            |enable/disable test multi pattern
|[SetCustFRC(scf)](#SetCustFRC)        |Set Out Frame Rate
|[OSTG in pattern(ostgpt)](#OSTG_in_pattern)|ostg paten
|[list(l)](#list)                |show panel list
|[query(q)](#query)               |dump pmx(scpos) info
|[set(s)](#set)                 |set parameter
|[post scaler(ps)](#post_scaler)        |set parameter
|[diag(d)](#diag)                |verify hardware
|[od(od)](#od)                 |od parameters
|[vopll(vopll)](#vopll)           |vopll parameters
|[dvopll(dvopll)](#dvopll)         |dvopll parameters
|[if(if)](#if)                 |lvds interface parameters
|[intr(intr)](#intr)             |interrupt
|[uhd(u)](#uhd)                 |uhd
|[pll(pll)](#pll)               |pll check
|[debug_on(d_on)](#debug_on)         |PMX.d_on
|[debug_off(d_off)](#debug_off)       |PMX.d_off
|[debug_level(d_l)](#debug_level)       |PMX.d_l

<h4 id="enable">enable(e)</h4>

开屏&关屏，常用于验证调的开关机时序是否OK，使用方法：e 0 / e 1
<h4 id="SetCustFRC">SetCustFRC(scf)</h4>

用于切换输出频率，使用方法：scf + 参数 可选参数为：
```
Usage: scf <CustFRCMask>
Set customized FRC
0x0: Normal
0x1: SUPPORT_50TO60_2D
0x2: SUPPORT_50TO60_3D
0x4: SUPPORT_60TO50_2D
0x8: SUPPORT_60TO50_3D
DTV.pmx>
```
<h4 id="list">list(l)</h4>

用于列出当前所有屏参。用法 `DTV.pmx>l`
<h4 id="set">set(s)</h4>

屏参相关参数调试，`DTV.pmx>cd s`按回车后：

|命令|命令解释|
|:-----------|:------------|
|[bg]                     |background color
|[po]                     |plane order
|[poa]                    |plane order array
|[pma](#pma)                    |plane mix alpha
|[backlt(bl)](#backlt)             |backlight
|[driving(d)](#driving)             |lvds driving current
|[vcm(vcm)](#vcm)               ||lvds common voltage
|[spread(s)](#spread)              |lvds spread spectrum
|[panel(p)](#panel)               |panel resolution
|[driverini(di)](#driverini)          |panel driver init
|[powersequence(ps)](#powersequence)      |adjust power sequence
|[ns(ns)](#ns)                 |NS lvds format
|[jeida(jeida)](#jeida)           |JEIDA lvds format
|[SpecialNs(sns)](#SpecialNs)         |Special NS lvds format
|[dnie(dnie)](#dnie)             |ByPass DNIE
|[10bit(10bit)](#10bit)           |switch LVDS to 10bit
|[swap(swap)](#swap)             |even odd channel swap
|[lvdsmod](#)                |set LVDS Tx mode
|[qlvdsmod](#)               |query LVDS Tx mode
|[SetCtrlWordStep(cws)](#)   |Nptv Set Control Word Step
|[OutputStageDumpEnable(os   |Enable OutputStage Dump
|[ForceFrameRate(ffr)](#)    |Nptv force frame rate
|[ForceFreeRun(fr)](#)       |Nptv force free run
|[borderonoff(boo)](#)       |OSTG border
|[bordercolor(bc)](#)        |OSTG border color
|[borderparameter(bparam)](#)|OSTG border position
|[panelifmask(pim)](#)       |Set Panel interface allowed mask
|[ATERM_ATVO(ATERM_ATVO)](#) |PmxLVDS_ATERM_ATVO_Setting
|[ATERM_ATVO_Restore(ATERMPmx|LVDS_ATERM_ATVO_Restore
|[ATVO_Set(ATVO_Set)](#)     |PmxLVDS_ATVO_Set
|[APSRC_Set(APSRC_Set)](#)   |PmxLVDS_APSRC_Set
|[ANSRC_Set(ANSRC_Set)](#)   |PmxLVDS_ANSRC_Set
|[PADPD_Set(PADPD_Set)](#)   |PmxLVDS_PADPD_Set
|[RESET_Set(RESET_Set)](#)   |PmxLVDS_RESET_Set
|[LS_Set(LS_Set)](#)         |PmxMLVDS_LS_Set
|[TestMODE_Set(TestMODE_Se   |PmxMLVDS_TestMODE_Set
|[VCOPhase_SEL(VCOPhase_SE   |PmxDrvVCOPhase_SEL
|[DDDSFreeRun(DDDSFreeRun)   |PmxSET_DDDSFreeRun
|[DDDSErrorLimit(dddsel)](#) |PmxSET_DDDSErrorLimit
|[controlword(ctlw)](#)      |Set control word
|[controlword2(ctlw2)](#)    |Set control word2
|[scanningpwm(scanpwm)](#)   |Set scanning pwm
|[scanstatus(scanpwms)](#)   |Get scanning status
|[scanstep(scanstep)](#)     |Set scanning step control
|[scantarget(scantarget)](#) |Set scanning step target


