
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
|[vdp](#vdp)                      |Video plane command
|[prescale](#prescale)                 |Prescale cmd
|[fbm](#fbm)                      |Frame buffer manager command
|[dbs](#dbs)                      |Dbs command
|[tcon](#tcon)                     |Tcon command
|[ptp](#ptp)                      |PTP control command
|[dmx(d)](#dmx)                   |Demux commands
|[memtest](#memtest)                  |Memory test
|[cec](#cec)                      |HDMI CEC test
|[cbus](#cbus)                     |HDMI CBUS test
|[pdwnc(pdwnc)](#pdwnc)             |PDWNC commands
|[gpio](#gpio)                     |Gpio interface
|[tve](#tve)                      |Tve command
|[timeprofile](#timeprofile)              |timeprofile test
|[bim](#bim)                      |BIM module test
|[pcmcia(p)](#pcmcia)                |Pcmcia command
|[gfx](#gfx)                    |Gfx command

第一级别命令用法解释
=====
<h4 id="cd">cd</h4>

`cd` 命令用来打开每一层级的功能列表，可以看做是打开文件夹。
<h4 id="do">do</h4>

`do` 命令用来再次输入前一次的命令。
<h4 id="alias">alias</h4>

`alias` 用于对你常用的命令取别名。一般不常用，因为这个别名存储在本地设备，我们一般调试完一台机器就完了，频次不高，没有设置别名的需求。
<h4 id="pmx">pmx</h4>

`pmx` 命令用来修改屏参，PQ相关的参数。[详见](#pmx2)

---
---

第二级别命令用法解释
=====
<h4 id="pmx2">DTV.pmx</h4>

|命令|命令解释|
|:---------|:----------|
|init(i):                |init
|enable(e):              |enable/disable LVDS
|pattern(p):             |enable/disable test pattern
|pat chg(pc):            |enable/disable test multi pattern
|SetCustFRC(scf):        |Set Out Frame Rate
|OSTG in pattern(ostgpt):|ostg paten
|list(l):                |show panel list
|query(q):               |dump pmx(scpos) info
|set(s):                 |set parameter
|post scaler(ps):        |set parameter
|diag(d):                |verify hardware
|od(od):                 |od parameters
|vopll(vopll):           |vopll parameters
|dvopll(dvopll):         |dvopll parameters
|if(if):                 |lvds interface parameters
|intr(intr):             |interrupt
|uhd(u):                 |uhd
|pll(pll):               |pll check
|debug_on(d_on):         |PMX.d_on
|debug_off(d_off):       |PMX.d_off
|debug_level(d_l):       |PMX.d_l

<h4 id="enable">enable</h4>

开屏&关屏，常用于验证调的开关机时序是否OK，使用方法：e 0 / e 1

