
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
<h4 id="alias">alias(a)</h4>

`alias` 用于对你常用的命令取别名。一般不常用，因为这个别名存储在本地设备，我们一般调试完一台机器就完了，频次不高，没有设置别名的需求。**可以使用括号中的简写代替本条命令~**
<h4 id="ls">ls</h4>

`ls` 命令用来列出本页所有可用命令，直接按 `Enter` 也是一样的效果。
<h4 id="read">read(r)</h4>

`read` 命令
<h4 id="write">write(w)</h4>

`write` 命令
<h4 id="customer">customer(cust)</h4>

`customer` 命令
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

`timeprofile` 命令
<h4 id="bim">bim</h4>

`bim` 命令
<h4 id="pcmcia">pcmcia(p)</h4>

`pcmcia` 命令
<h4 id="os">os</h4>

`os` 命令
<h4 id="linux">linux</h4>

`linux` 命令
<h4 id="gfx">gfx</h4>

`gfx` 命令
<h4 id="imgrz">imgrz</h4>

`imgrz` 命令

---
---

第二级别命令用法解释
=====
<h4 id="pmx2">DTV.pmx</h4>

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

<h4 id="enable">enable</h4>

开屏&关屏，常用于验证调的开关机时序是否OK，使用方法：e 0 / e 1

