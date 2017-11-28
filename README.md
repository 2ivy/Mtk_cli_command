
本文列举的当前会遇到的所有cli命令
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
|[cd](#cd)                     |Change current directory|
|[do](#do)                     |Repeat command|
|[alias(a)](#alias)               |Add/Show current alias|
|[ls](#ls)                   |Recursive list all commands|
|read(r)                |Memory read(word)|
|[write(w)](#write)                 |Memory write(word)|
|customer(cust)           |Get customer name|
|basic_(b)                |basic command|
|linuxmode(l)             |Turn on/off linux mode|
|mtktool(0)               |mtktool command|
|osd                      |Osd driver|
|[pmx](#pmx)                     |pmx command|
|sif                      |Sif command|
|[pwm](#pwm)                      |Pwm command|
|[eeprom](#eeprom)                   |Eeprom command|
|nim                      |Nim command|
|ir                       |Ir command|
|rtc(rtc)                 |RTC commands
|[aud](#aud)                      |Aud command
|nptv(n)                  |Nptv command
|vdp                      |Video plane command
|prescale                 |Prescale cmd
|fbm                      |Frame buffer manager command
|dbs                      |Dbs command
|tcon                     |Tcon command
|[ptp](#ptp)                      |PTP control command
|dmx(d)                   |Demux commands
|memtest                  |Memory test
|cec                      |HDMI CEC test
|cbus                     |HDMI CBUS test
|pdwnc(pdwnc)             |PDWNC commands
|gpio                     |Gpio interface
|tve                      |Tve command
|timeprofile              |timeprofile test
|bim                      |BIM module test
|pcmcia(p)                |Pcmcia command
|gfx                    |Gfx command


第一级别命令用法解释
=====
<h4 id="cd">cd</h4>

`cd` 命令用来打开每一层级的命令页。
<h4 id="do">do</h4>

`do` 命令用来再次输入前一次的命令。
<h4 id="alias">alias(a)</h4>

`alias` 用于对你常用的命令取别名。目前已经对很多较长的命令设置了别名，括号中的的简写就是，**可以使用括号中的简写代替单条命令**。
<h4 id="ls">ls</h4>

`ls` 命令用来列出所有可用命令，直接按 `Enter`则是列出当前页所有命令。
<h4 id="write">write</h4>

`write` + 具体内存地址，配合其他指令可以实现特定的功能。比如[查看CPU温度](#getCPUTmp)

<h4 id="customer">customer(cust)</h4>

`customer` 用于获取客户名称，作用如下。

	DTV>cust
	[cmtk / mtk]
	DTV>
	
<h4 id="pmx">pmx</h4>

`pmx` 命令用来修改屏参，PQ相关的参数。[详见](#pmx2)
<h4 id="eeprom">eeprom</h4>

`eeprom` 命令，这个命令直接操作寄存器，目前用到主要是在换屏参时候。[详见](#panel)
<h4 id="aud">aud</h4>

`aud` 命令用来调试声音相关的，比较重要的一个命令。[详见](#aud2)
<h4 id="ptp">ptp</h4>

`ptp` 可以执行一系列的PTP指令集，需要配合其他命令一起使用，<p4 id="getCPUTmp">获取CPU温度</p4>：

	DTV>w 0xf0028304 0xfffff809
	DTV>ptp.t
会返回

	CPU temp = 60200
结果除以1000就是实际温度，如上是60度，一般TV下播放且散热正常的情况下基本小于80度，遇到莫名其妙一直重启的问题，可以先读取下节点温度，芯片设置大于**115度**时会自动重启。

---
---

第二级别命令用法解释
=====
<h3 id="pmx2">DTV.pmx</h3>

|命令|命令解释|
|:---------|:----------|
|init(i)                |init
|[enable(e)](#enable)              |enable/disable LVDS
|pattern(p)             |enable/disable test pattern
|pat chg(pc)            |enable/disable test multi pattern
|[SetCustFRC(scf)](#SetCustFRC)        |Set Out Frame Rate
|OSTG in pattern(ostgpt)|ostg paten
|[list(l)](#list)                |show panel list
|query(q)               |dump pmx(scpos) info
|[set(s)](#set)                 |set parameter
|[post scaler(ps)](#post_scaler)        |set parameter
|diag(d)                |verify hardware
|od(od)                 |od parameters
|vopll(vopll)           |vopll parameters
|dvopll(dvopll)         |dvopll parameters
|if(if)                 |lvds interface parameters
|intr(intr)             |interrupt
|uhd(u)                 |uhd
|pll(pll)               |pll check
|debug_on(d_on)         |PMX.d_on
|debug_off(d_off)       |PMX.d_off
|debug_level(d_l)       |PMX.d_l

<h4 id="enable">enable(e)</h4>

开屏&关屏，常用于验证调的开关机时序是否OK，使用方法：
	
	DTV.pmx>e 0 //关屏
	DTV.pmx>e 1 //开屏

<h4 id="SetCustFRC">SetCustFRC(scf)</h4>

用于切换输出频率，使用方法：scf + 参数 可选参数为：

	DTV.pmx>scf
	Usage: scf <CustFRCMask>
	Set customized FRC
	0x0: Normal
	0x1	: SUPPORT_50TO60_2D
	0x2: SUPPORT_50TO60_3D
	0x4: SUPPORT_60TO50_2D
	0x8: SUPPORT_60TO50_3D
	DTV.pmx>

<h4 id="list">list(l)</h4>

用于列出当前所有屏参。用法 `DTV.pmx>l`,会列出当前所有存在的屏参文件~
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
|vcm(vcm)               |lvds common voltage
|[spread(s)](#spread)              |lvds spread spectrum
|[panel(p)](#panel)               |panel resolution
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

	DTV.pmx.s>bl
	Args: backlight(0~255) [freq(Hz)]
	CLI Command Return Value (-1)
	DTV.pmx.s>

<h4 id="driving">driving(d)</h4>

调节驱动电流，例如：d 8。合法构造如下：

	DTV.pmx.s>d
	current value=5
	Args: value(0~15)	
	CLI Command Return Value (-1)
	DTV.pmx.s>

<h4 id="spread">spread(s)</h4>

调节lvds频展，例如：s 30 30 【工厂菜单可调节】。合法构造如下：

	DTV.pmx.s>spread
	current range = 40
	current modulation rate = 30000
	Args: {value(20K~100K), value(0~60)} | {rate(Hz), range(0.1%)}
	CLI Command Return Value (-1)
	DTV.pmx.s>
<h4 id="panel">panel(p)</h4>

更换屏参命令，可更换的屏参列表见[pmx.s.l](#list)命令。panel命令使用的方法是直接`p + 序号`，但是注意这个是更换屏参的第二步，第一步需要使用[epprom](#eeprom)命令清除屏参的寄存器`eeprom.bw 0x1429 0xfe 4`。

<h4 id="powersequence">powersequence(ps)</h4>

调节开关时序，例如：ps 10 20 30 40，调完后使用上面提到的[开关屏命令](#enable)验证，注意，**开关机是不保存**的。合法构造如下：

	DTV.pmx.s>ps
	Args: LvdsOn, BacklightOn, BacklightOff, LvdsOff (unit:10ms)
	CLI Command Return Value (-1)
	DTV.pmx.s>

<h4 id="ForceFrameRate">ForceFrameRate(ffr)</h4>

调节输出频率，例如：ffr 50。合法构造如下：

	DTV.pmx.s>ffr
	Arg: ubFrameRage, 0:disable
	DTV.pmx.s>

---

<h4 id="post_scaler">post scaler(ps)</h4>

调节屏参里的HTotal、VTotal、Clock等，相关信息如下：

|命令|命令解释|
|:---------------|:---------------|
|[query status(q)](#query_status)        |query post scaler status
|[ps hsynctest(ht)](#ps_hsynctest)       |hsync scaler timing test
|[ps vsynctest(vt)](#ps_vsynctest)       |vsync scaler timing test
|ps set_data trigger(st) |set data trigger

<h4 id="query_status">query status(q)</h4>

查询当前的HTotal、VTotal、Clock、out frame rate 等，方法`DTV.pmx.ps>q`

<h4 id="ps_hsynctest">ps hsynctest(ht)</h4>

可操作参数信息如下，分别是调节HTotal、Frontporch、Backporch：

	DTV.pmx.ps>vt
	Arg: ucOnOff  (Panel Vsync Test)
	type [0] Sync Width change
	type [1] Sync Front porch change
	type [2] Sync Back porch change

例如 输入 `DTV.pmx.ps>ht 1` 进入 `Htotal` 调试界面

	DTV.pmx.ps>ht 1
	Begin to panel Hsync test
	Htotal=2200, Hfp=16,Hwid=30 HBp=234 Hactive=1920
	Please enter 'u' when do up test
	Please enter 'd' when do down test

如提示，按下**u键**表示数值会向上调整，按下**d键**表示数值会向下调整。按下**Esc键 + Enter键**退出调试。

<h4 id="ps_vsynctest">ps vsynctest(vt)</h4>

可操作参数信息如下，分别是调节VTotal、Frontporch、Backporch：

	DTV.pmx.ps>ht
	Arg: ucOnOff  type (Panel Hsync Test)
	type [0] Sync Width change
	type [1] Sync Front porch change
	type [2] Sync Back porch change

调试方法如上实例。

---
---

<h3 id="aud2">DTV.aud</h3>

`aud`命令页进入后

|命令|命令解释|
|:---------------|:---------------|
|init(i)                |Aud init
|debug_on(d_on)         |AUD.d_on
|debug_off(d_off)       |AUD.d_off
|debug_level(d_l)       |AUD.d_l
|setdec(s)              |Aud set decoding type
|resume                 |Aud resume
|pause                  |Aud pause
|play                   |Aud play
|stop                   |Aud stop
|dual(dual)             |dual
|tri(tridec)            |tri_dec
|sync                   |Aud sync mode setting
|stream(str)            |Playback stream src
|query(q)               |Audio status query
|m                      |Audio mixsound playback
|mclip                  |Audio mixsound clip playback
|pll1                   |Aud Pll1 setting
|pll2                   |Aud Pll2 setting
|pllpd                  |Aud Pll PoweDown
|dsp                    |dsp command
|[aproc(a)](#aproc)               |audio processor command
|iec(iec)               |IEC related command
|spost(spost)           |Spost related command
|[uop](#uop)                    |audio uop
|t                      |test
|Clip                   |Aud Clip
|atv                    |ATV command
|dtv                    |DTV command
|fmrdo                  |FM Radio command
|io                     |I/O command
|src                    |ASRC status query
|dram                   |DRAM command
|adecomx                |ADECOMX command
|syncdbg(sd)            |AV Sync Debug command
|dolby(db)              |Dolby related command
|pm                     |Query play mute history
|psrdbg(pd)             |Set HDMI Pre-Parser debug flag
|soundbar(sb)           |Watch sound bar register
|setdelay(setdelay)     |Set Vdep Delay Tbl
|SpeedTest(speed)       |mm playback speed test
|User mode set(mode)    |set user mode HP/LO
|querybuffer(qb)        |query all audio buffer
|util(util)             |audio util
|aq(aq)                 |audio aq
|suspend resume(sr)     |suspend resume audio
|trace(trace)           |audio trace level switch

<h4 id="uop">uop</h4>

`uop`命令

|命令|命令解释|
|:---------------|:---------------|
|DSP volume system(qv)  |DSP volume system setting
|fine volume(fv)        |Audio Master Volume fine control
|volume(v)              |Audio Volume control
|vol_curve(vc)          |Audio Volume Curve Set
|vol_curve_query(vcq)   |Audio Volume Curve Query
|set volume table(svt)  |Audio Volume table set
|fine ch volume(fcv)    |Audio Channel Volume fine control
|ch volume(cv)          |Audio Channel Volume control
|[ch vol gain(cvg)](#ch_vol_gain)       |Audio Channel Volume Gain control
|[src volume(sv)](#src_volume)         |Audio Source Volume control
|[src volume query(svq)](#src_volume_query)  |Query Audio Source Volume
|equalizer(eq)          |EQ configuration
|sbass(sbass)           |Bass/treble configuration
|Silence set(silence)   |Slience fuction set
|limiter(limiter)       |Limiter configuration
|pl2cfg(pl2cfg)         |Prologic 2 related configuration
|spkuop(spkuop)         |Speaker related configuration
|AVC(a)                 |Automatic Volume Control
|MonoDownmix(md)        |Downmix to mono
|Karaoke mix ratio(kr)  |Karaoke mix ratio
|balance(bl)            |Set L/R balance
|virtualsurround(vs)    |Virtual Surround flag
|vsurround config(vscfg)|Virtual Surround Config
|peq(peq)               |Set PEQ
|peqc(peqc)             |Set PEQ Configuration
|peqc2(peqc2)           |Set PEQ Configuration
|FF SPEED(speed)        |DSP Speed
|DMixPos(dmp)           |Downmix channel position
|MultiPair(MultiPair)   |Multi-Pair output
|LR DownMix(LRDMix)     |LR DownMix
|dump(dump)             |DSP Dump
|DDCO(DDCO)             |DDCO setting
|DDCO AGC(DDCOAgc)      |DDCO AGC setting
|DDCO LFE LFP(DDCOLFE)  |DDCO AGC setting
|dualmono(dm)           |dual-mono steup
|EAC3(eac3)             |E-ac3 raw enable
|upload(up)             |Upload data enable
|uploadinit(upi)        |Upload data init
|uploaddump(upd)        |Upload data dump
|encmode(enc)           |Set Encode mode
|adupdate(adupdate)     |ad fade pan update setup
|adfade(adfade)         |ad fade setup
|adpan(adpan)           |ad pan setup
|adpanfaden(adpanfaden) |ad pan fade enable
|sbcdump(sbcd)          |SBC Encode Test
|adcdump(adcd)          |SBC Encode Test
|postq(pq)              |Post-Proc Query
|g726dec(g726dec)       |G726 decoder setting
|check sum pbD(csum)    |check sum _pbD

<h4 id="src_volume_query">svq</h4>

查询各个通道的prescale数值。如何设置prescale？[点我](#sv)
<h4 id="src_volume">sv</h4>

设置prescale命令，命令组成为：sv + 解码器ID + 通道 + 数值

	Usage: sv [decoder id] [source] [value]
	[decoder id] 0:FIRST 1:SECOND 2:THIRD 3: 4TH
	[source #]      0:OTHERS, 1:DIGITAL, 2:ANALOG, 3:SPDIF
                    4:LINE_IN, 5:HDMI, 6:MEMORY 7: BUFAGT 8: FEEDER 9: MM
                   10:LINE_IN2, 11:LINE_IN3
	[volume]        -128~36     every 0.5dB per step
                  -128:  -64    dB
                  -127:  -63.5 dB
                  -126:  -63    dB
                     .       .
                     .       .
                     .       .
                     0:    0     dB
                     .       .
                     .       .
                     .       .
                    36:   18   dB
	CLI Command Return Value (-1)

例如设置DTV prescal值为3：sv 0 1 3
<h4 id="ch_vol_gain">cvg</h4>

可以通过 `DTV.aud.uop>cvg q` 查询各个频道的LinOut幅值。
`DTV.aud.uop>cvg`命令信息有:

    Usage: cvg [decoder id] [channel] [gain] or cvg q
    [decoder id]     0:FIRST                 1:SECOND
    [channel #]      0:L, 1:R, 2:LS, 3:RS, 4:C, 5:SUBWOOFER,
                     6:Bypass L, 7: Bypass R, 8: Downmix L, 9: Dowmix R
    [gain]           -128 ~ 96,  every 0.5dB per step
                     -128:  -64   dB
                     -127:  -63.5 dB
                     -126:  -63   dB
                         .        .
                         .        .
                         .        .
                        0:    0   dB
                        1:    0.5 dB
                         .        .
                         .        .
                       96:   48   dB
    CLI Command Return Value (-1)

设置lineout幅度命令为：cvg 0 6 2   (这里比较特别的是，设置了一边声道之后另外一边也跟着生效的，所以调试的时候只需要调一边声道就可以)

<h4 id="aproc">aproc(a)</h4>

|命令|命令解释|
|:---------------|:---------------|
|init(i)                |aproc task init ex. init
|pc                     |Get aproc pc ex. pc
|reads(r)               |Read aproc ex. reads [addr]
|writes(w)              |Write aproc ex. write [addr] [data]
|open(o)                |command: open
|close(c)               |command: close
|notifyadsp(nod)        |command: notify adsp
|writeadsp(wd)          |command: write adsp
|regread(rr)            |Reg read aproc ex. reads [addr]
|refwrite(rw)           |Reg write aproc ex. write [addr] [data]
|qmem(qm)               |memory map query
|enable(enable)         |enable/disable audio processor
|ice(ice)               |connect ICE
|modctrl(modctrl)       |module control
|poweron(pon)           |aproc power-on
|powerdown(pdown)       |aproc power-down
|reset(reset)           |aproc reset test
|amxier(amx)            |audio processor amixer command
|admix(ad)              |post-processing AD mixing
|iec(iec)               |audio processor iec command
|query(q)               |query aproc
|mixsound(ms)           |Aproc MixSound Test
|upload(up)             |Aproc Upload Test
|riscpost(rp)           |Aproc RiscPost Test
|aproc(acmd)            |Ask APROC AVSync Command
|logid(ld)              |Print Log for which decoder
|syncinfo(si)           |List AVSync information
|2.2/4.0 sel(chs)       |2.2/4.0 out select
|amixer mute(am)        |amixer mute setting
|volume(vol)            |audio processor volume command
|[sound effect(se)](#sound_effect)       |audio processor sound effect command
|sound speed(speed)     |audio processor sound speed command
|Test DrvCust AQ(aq)    |Test Flash AQ
|DrvCust AQ Key(key)    |Test Flash AQ Key
|Fade In/Out(fade)      |Fade In / Fade Out Function
|queryGlobleInfo(qgi)   |get aproc globle def info
|bypass(b)              |Bypass dsp pro,data output directly

<h4 id="sound_effect">sound effect(se)</h4>

|命令|命令解释|
|:---------------|:---------------|
|[BassTreble(pbt)](#BassTreble)        |post-processing Bass Treble
|Balancer(blc)          |Balancer setting
|Bass Management(bmang) |Bass Managemant setting
|[SP AVC(avc)](#SP_AVC)            |Speaker Band0 AVC setting
|Virtual Surround(mvs)  |Virtual Surround Setting
|Virtual Bass(mvb)      |Virtual Bass setting
|PEQ(peq)               |PEQ setting
|[DRC Limiter(dl)](#DRC_Limiter)        |DRC limiter setting
|High Pass Filter(hpf)  |Speaker HPF setting
|EQ(eq)                 |EQ setting
|Eq Spectrum(spec)      |EQ spectrum enable
|monomix(monomix)       |post-processing Mono mixing
|postq(pq)              |post-processing query
|3 band DRC(3drc)       |3band DRC setting
|1 band DRC(1drc)       |1band DRC setting

<h4 id="DRC_Limiter">DRC Limiter(dl)</h4>


	Usage: dl [Idx][type][val]
	Idx         : Idx 0~3 : SP, SW, LSRS, HP
	Flag        : type= 0, val= 1 enable, = 0 disable,
	TargetLevel : type= 1, val= (0x7ff, 0x3fffff) -48dB ~ +18dB, 0x7ffff = 0dB
	AttackStep  : type= 2, val= (0x1, 0x7fffffff) 0.0000014 dB/ms ~ 192 dB/ms
	ReleaseStep : type= 3, val= (0x1, 0x7fffffff) 0.0000014 dB/ms ~ 192 dB/ms
	SetRatio    : type= 4, val= (0x0, 0x7ffff) 0x0= infinite:1, 0x7ffff = 1:1. Linear ratio
	SilenceLevel: type= 5, val= (0x0, 0x7ffff) 0x7= -96dB, 0x7ffff= 0dB, 0x0= no silenece level control Linear ratio
	MaxExpandGain:type= 6, val= (0x0, 0x7fffff) 0x2fffff= +6dB, 0x7fffff= +16dB, 0x7ffff= 1dB, 0x0= no expanding
	PostGain    : type= 7, val= (0x0, 0x7fffff) 0x0= off, 0x1 = -102 dB, 0x7fffff = 36dB
	HoldPeriod  : type= 8, val= (0x0, 0x1000) 0x0 = 0 ms, 0x200 = 5.46 s. Step = 1.33 ms
	DetPeriod   : type= 9, val= (0x0, 0x1000) 0x0 = 0 ms, 0x200 = 5.46 s. Step = 1.33 ms
	ProcMode    : type= a, val=
	SgainPeriod : type= b, val= (0x0, 0x1000) 0x0 = 0 ms, 0x200 = 5.46 s. Step = 1.33 ms
	CLI Command Return Value (-1)

Idx：不同通道，喇叭耳机
主要关注TargetLevel，就是drc值
例如调整耳机drc值：dl [Idx][type][val]                dl 3 1 0x6ffff

<h4 id="SP_AVC">SP AVC(avc)</h4>


	DTV.aud.a.se>avc
	[Query Info]AVC Enable: 0x0
	TargetLevel: 0x13000, AttackRate: 0xfffff, ReleaseRate: 0x800, MaxExpand 0x0
	Usage1: avc [item] [val]
      	    item select => TargetLevel:0 AttackRate:1
    	    item select => ReleaseRate:2 MaxExpand:3
       	    val => TargetLevel  (0x7ff, 0x3fffff) -48dB ~ +18dB, 0x7ffff = 0dB
       	    val => AttackRate   (0x1, 0x7fffffff) 0.0000014 dB/ms ~ 192 dB/ms
       	    val => ReleaseRate  (0x1, 0x7fffffff) 0.0000014 dB/ms ~ 192 dB/ms
      	    val => MaxExpand    (0x7ffff, 0x7ffff0) 0x9ffff = +2dB, 0xfffff= +6dB, 0x7ffff= 0dB, no expanding
	Usage2: avc [Flag]
         	Flag => On:0x1, Off: 0x0
	CLI Command Return Value (-1)

开关：avc 0x1、avc 0x0
设置参数：avc [item] [val]    //按照上图提示设置对应值，例如avc 0 0x12000
对应代码位置（5510目前avc是关闭的）：

<h4 id="BassTreble">BassTreble(pbt)</h4>

高低音的调节
喇叭调整SP Bass、SP Treble，耳机调整HP Bass、HP Treble
Type：滤波器类型，LSF_HI和HSF_HI没写出来，分别是0x103/0x104
Fc：中心频率
Q：影响范围
Gain：增益
用法：pbt 0 0x103 300 0x300000 0
