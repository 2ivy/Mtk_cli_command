
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
|read(r)                |Memory read(word)
|write(w)                 |Memory write(word)
|customer(cust)           |Get customer name
|basic_(b)                |basic command
|linuxmode(l)             |Turn on/off linux mode
|mtktool(0)               |mtktool command
|osd                      |Osd driver
|[pmx](#pmx)                     |pmx command
|sif                      |Sif command
|[pwm](#pwm)                      |Pwm command
|[eeprom](#eeprom)                   |Eeprom command
|nim                      |Nim command
|ir                       |Ir command
|rtc(rtc)                 |RTC commands
|[aud](#aud)                      |Aud command
|nptv(n)                  |Nptv command
|av                     |Audio/Video command
|vdp                      |Video plane command
|prescale                 |Prescale cmd
|fbm                      |Frame buffer manager command
|dbs                      |Dbs command
|mpv                    |MPEG Video Decoder command
|vdec                   |Vdec command
|tcon                     |Tcon command
|ptp                      |PTP control command
|muxer(mx)              |MUXER command
|dmx(d)                   |Demux commands
|memtest                  |Memory test
|cec                      |HDMI CEC test
|cbus                     |HDMI CBUS test
|pdwnc(pdwnc)             |PDWNC commands
|jpg                    |Jpeg command
|gpio                     |Gpio interface
|mid                    |Memory intrusion detection
|swdmx                  |SWDMX command
|feeder                 |FEEDER command
|tve                      |Tve command
|timeprofile              |timeprofile test
|bim                      |BIM module test
|pcmcia(p)                |Pcmcia command
|os                     |OS command
|linux                  |Linux commands
|gfx                    |Gfx command
|imgrz                  |Imgrz command


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
<h4 id="customer">customer(cust)</h4>

`customer` 用于获取客户名称
<h4 id="pmx">pmx</h4>

`pmx` 命令用来修改屏参，PQ相关的参数。[详见](#pmx2)
<h4 id="eeprom">eeprom</h4>

`eeprom` 命令
<h4 id="aud">aud</h4>

`aud` 命令

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
|bg                     |background color
|po                     |plane order
|poa                    |plane order array
|pma                    |plane mix alpha
|[backlt(bl)](#backlt)             |backlight
|[driving(d)](#driving)             |lvds driving current
|vcm(vcm)               ||lvds common voltage
|[spread(s)](#spread)              |lvds spread spectrum
|panel(p)               |panel resolution
|driverini(di)          |panel driver init
|[powersequence(ps)](#powersequence)      |adjust power sequence
|ns(ns)                 |NS lvds format
|jeida(jeida)           |JEIDA lvds format
|SpecialNs(sns)         |Special NS lvds format
|dnie(dnie)             |ByPass DNIE
|10bit(10bit)           |switch LVDS to 10bit
|swap(swap)             |even odd channel swap
|lvdsmod                |set LVDS Tx mode
|qlvdsmod               |query LVDS Tx mode
|SetCtrlWordStep(cws)   |Nptv Set Control Word Step
|OutputStageDumpEnable(os   |Enable OutputStage Dump
|[ForceFrameRate(ffr)](#ForceFrameRate)    |Nptv force frame rate
|ForceFreeRun(fr)       |Nptv force free run
|borderonoff(boo)       |OSTG border
|bordercolor(bc)        |OSTG border color
|borderparameter(bparam)|OSTG border position
|panelifmask(pim)       |Set Panel interface allowed mask
|[ATERM_ATVO(ATERM_ATVO) |PmxLVDS_ATERM_ATVO_Setting
|ATERM_ATVO_Restore(ATERMPmx|LVDS_ATERM_ATVO_Restore
|ATVO_Set(ATVO_Set)     |PmxLVDS_ATVO_Set
|APSRC_Set(APSRC_Set)   |PmxLVDS_APSRC_Set
|ANSRC_Set(ANSRC_Set)   |PmxLVDS_ANSRC_Set
|PADPD_Set(PADPD_Set)   |PmxLVDS_PADPD_Set
|RESET_Set(RESET_Set)   |PmxLVDS_RESET_Set
|LS_Set(LS_Set)         |PmxMLVDS_LS_Set
|TestMODE_Set(TestMODE_Se   |PmxMLVDS_TestMODE_Set
|VCOPhase_SEL(VCOPhase_SE   |PmxDrvVCOPhase_SEL
|DDDSFreeRun(DDDSFreeRun)   |PmxSET_DDDSFreeRun
|DDDSErrorLimit(dddsel) |PmxSET_DDDSErrorLimit
|controlword(ctlw)      |Set control word
|controlword2(ctlw2)    |Set control word2
|scanningpwm(scanpwm)   |Set scanning pwm
|scanstatus(scanpwms)   |Get scanning status
|scanstep(scanstep)     |Set scanning step control
|scantarget(scantarget) |Set scanning step target

<h4 id="backlt">backlt(bl)</h4>

backlight 调节背光，例如：bl 255 200。合法构造如下：
```
DTV.pmx.s>bl
Args: backlight(0~255) [freq(Hz)]
CLI Command Return Value (-1)
DTV.pmx.s>
```
<h4 id="driving">driving(d)</h4>

调节驱动电流，例如：d 8。合法构造如下：
```
DTV.pmx.s>d
current value=5
Args: value(0~15)
CLI Command Return Value (-1)
DTV.pmx.s>
```
<h4 id="spread">spread(s)</h4>

调节lvds频展，例如：s 30 30 【工厂菜单可调节】。合法构造如下：
```
current range = 40
current modulation rate = 30000
Args: {value(20K~100K), value(0~60)} | {rate(Hz), range(0.1%)}
CLI Command Return Value (-1)
DTV.pmx.s>
```
<h4 id="powersequence">powersequence(ps)</h4>

调节开关时序，例如：ps 10 20 30 40，调完后使用上面提到的开关屏命令验证，注意，开关机是不保存的。合法构造如下：
```
Args: LvdsOn, BacklightOn, BacklightOff, LvdsOff (unit:10ms)
CLI Command Return Value (-1)
DTV.pmx.s>
```
<h4 id="ForceFrameRate">ForceFrameRate(ffr)</h4>

调节输出频率，例如：ffr 50。合法构造如下：
```
Arg: ubFrameRage, 0:disable
DTV.pmx.s>
```

---

<h3 id="post_scaler">post scaler(ps)</h4>

调节屏参里的HTotal、VTotal、Clock等，相关信息如下：
|命令|命令解释|
|:--------------|:-------------|
|[query status(q)](#query_status)        |query post scaler status
|[ps hsynctest(ht)](#ps_hsynctest)       |hsync scaler timing test
|[ps vsynctest(vt)](#ps_vsynctest)       |vsync scaler timing test
|[ps set_data trigger(st)](#ps_set_data_trigger) |set data trigger

<h4 id="query_status">query status(q)</h4>

查询当前的HTotal、VTotal、Clock、out frame rate 等，方法`DTV.pmx.ps>q`

<h4 id="ps_hsynctest">ps hsynctest(ht)</h4>

可操作参数信息如下，分别是调节HTotal、Frontporch、Backporch：
```
DTV.pmx.ps>vt
Arg: ucOnOff  (Panel Vsync Test)
type [0] Sync Width change
type [1] Sync Front porch change
type [2] Sync Back porch change
```
例如 输入 `DTV.pmx.ps>ht 1` 进入 `Htotal` 调试界面
```
DTV.pmx.ps>ht 1
Begin to panel Hsync test
Htotal=2200, Hfp=16,Hwid=30 HBp=234 Hactive=1920
Please enter 'u' when do up test
Please enter 'd' when do down test
```
如提示，按下**u键**表示数值会向上调整，按下**d键**表示数值会向下调整。按下**Esc键 + Enter键**退出调试。

<h4 id="ps_hsynctest">ps hsynctest(ht)</h4>

可操作参数信息如下，分别是调节VTotal、Frontporch、Backporch：
```
DTV.pmx.ps>ht
Arg: ucOnOff  type (Panel Hsync Test)
type [0] Sync Width change
type [1] Sync Front porch change
type [2] Sync Back porch change
```
调试方法如上实例。
