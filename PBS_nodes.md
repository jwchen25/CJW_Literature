cat /proc/cpuinfo  # 查看CPU
cat /proc/meminfo  # 查看内存
lspci | grep -i nvidia  # 查看GPU
pbsnodes -l free  # 查看空闲节点
qstat -f 任务号  # 查看指定任务运行详细情况，如运行节点，运行文件位置等

IB1       :  node1 -node14  np=8  //  CPU: Intel(R) Xeon(R) E5620 @ 2.40GHz; Memory: 24GB
IB2       :  node15-node29  np=24  //  CPU: Intel(R) Xeon(R) E5-2692v2 @ 2.20GHz; Memory: 64GB
IB2(GPU)  :  node30-node34  np=24  //  CPU: Intel(R) Xeon(R) E5-2692v2 @ 2.20GHz; Memory: 64GB; GPU: NVIDIA Tesla K20m
IB3       :  node35-node46  np=24  //  CPU: Intel(R) Xeon(R) E5-2680v3 @ 2.50GHz; Memory: 64GB
IB4       :  node47-node51  np=32  //  CPU: Intel(R) Xeon(R) E5-2682v4 @ 2.50GHz; Memory: 128GB
IB4(SINO) :  node52-node54  np=32  //  CPU: Intel(R) Xeon(R) E5-2682v4 @ 2.50GHz; Memory: 128GB
SINO      :  node55-node58  np=32  //  CPU: Intel(R) Xeon(R) E5-2682v4 @ 2.50GHz; Memory: 128GB
IB5(SINO) :  node59-node61  np=32  //  CPU: Intel(R) Xeon(R) E5-2682v4 @ 2.50GHz; Memory: 64GB
IB5       :  node62-node74  np=32  //  CPU: Intel(R) Xeon(R) E5-2682v4 @ 2.50GHz; Memory: 64GB
IB5(LMEM) :  node75-node76  np=32  // LMEM : Larger memory (about 280GB)
IB5(new)  :  node77-node84  np=40  //  CPU: Intel(R) Xeon(R) Gold 6230 @ 2.10GHz; Memory: 128GB

Q_SINO    :   4 nodes  np=32
Q_IB1     :  14 nodes  np= 8
Q_IB2     :  20 nodes  np=24
Q_IB3     :  12 nodes  np=24
Q_IB4     :   8 nodes  np=32
Q_IB5     :  18 nodes  np=32
IB5(new)  :   8 nodes  np=40




Queue: Q_SINO
    queue_type = Execution
    total_jobs = 4
    state_count = Transit:0 Queued:0 Held:0 Waiting:0 Running:4 Exiting:0 Comp
	lete:0 
    acl_host_enable = True
    acl_hosts = master
    acl_user_enable = True
    acl_users = xqyao
    resources_default.nodes = 1
    resources_default.walltime = 9600:00:00
    mtime = 1600756787
    resources_assigned.nodect = 4
    enabled = True
    started = True

Queue: Q_IB1
    queue_type = Execution
    total_jobs = 5
    state_count = Transit:0 Queued:1 Held:0 Waiting:0 Running:4 Exiting:0 Comp
	lete:0 
    acl_host_enable = True
    acl_hosts = master
    acl_user_enable = True
    acl_users = chbin,chengye,chenpan,chlwang,cosmoilc,dgwang,dingjian,dingwl,dlgao,
	dongkun,fhuo,fyan,fyang,haoli,huty,hyhe,jfwang,jhtong,jyhe,jyqin,khzhang,klbi,
	kzzhang,lijin,liulei,liwei,lixl,longliu,lwang,mafei,mchwang,mgong,miwang,msi,
	qfli,qiancheng,rbbai,sguo,sswang,supersun,sxchen,tanxin,thyu,tsong,tzhang,wuzw,
	wzhsun,xchzhang,xhwu,xiexiaodong,xqyao,yanhw,yaoli,ybliu,yfsun,ylwang,youll,
	yqzhang,ytian,yuke,ywli,yxia,yxyang,yyzhao,zdgan,zhangtao,zhangyou,zhuyx,
	zlwang,znzhong,zyju
    resources_default.nodes = 1
    resources_default.walltime = 7200:00:00
    mtime = 1600756787
    resources_assigned.nodect = 5
    enabled = True
    started = True

Queue: Q_IB5
    queue_type = Execution
    total_jobs = 23
    state_count = Transit:0 Queued:11 Held:0 Waiting:0 Running:12 Exiting:0 Co
	mplete:0 
    acl_host_enable = True
    acl_hosts = master
    acl_user_enable = True
    acl_users = bwli,chengye,chlwang,cosmoilc,dgwang,dingjian,dingwl,dlgao,dongkun,
	fhuo,fyan,huty,hyhe,jfwang,jhtong,jyqin,khzhang,klbi,lijin,liulei,liwei,lixl,
	mchwang,mgong,miwang,msi,qfli,qiancheng,sswang,supersun,sxchen,tanxin,tzhang,
	wuzw,wzhsun,xchzhang,xhwu,xiexiaodong,xqyao,yanhw,yaoli,ylwang,yqzhang,yuke,
	yxia,yxyang,yyzhao,zdgan,zhangtao,zhuyx,zlwang,zyju
    resources_default.nodes = 1
    resources_default.walltime = 7200:00:00
    mtime = 1600756787
    resources_assigned.nodect = 14
    enabled = True
    started = True

Queue: batch
    queue_type = Execution
    total_jobs = 0
    state_count = Transit:0 Queued:0 Held:0 Waiting:0 Running:0 Exiting:0 Comp
	lete:0 
    acl_user_enable = True
    acl_users = fhuo
    resources_default.nodes = 1
    resources_default.walltime = 7200:00:00
    mtime = 1600937232
    enabled = True
    started = True

Queue: Q_IB3
    queue_type = Execution
    total_jobs = 14
    state_count = Transit:0 Queued:4 Held:0 Waiting:0 Running:10 Exiting:0 Com
	plete:0 
    acl_host_enable = True
    acl_hosts = master
    acl_user_enable = True
    acl_users = chbin,dongkun,fyang,jwchen,jyhe,kzzhang,liulei,mafei,sguo,thyu@master,
	xchzhang,xfma,xjwang,xli,xqyao,xyyao@master,yaoli,yfsun,youll,ytian,ytliu,zyju
    resources_default.nodes = 1
    resources_default.walltime = 7200:00:00
    mtime = 1600756787
    resources_assigned.nodect = 11
    enabled = True
    started = True

Queue: Q_IB4
    queue_type = Execution
    total_jobs = 9
    state_count = Transit:0 Queued:2 Held:0 Waiting:0 Running:7 Exiting:0 Comp
	lete:0 
    acl_host_enable = True
    acl_hosts = master
    acl_user_enable = True
    acl_users = bwli,dongkun,fyang,jliu,jwchen,jyhe,kzzhang,liulei,mafei,msi,sguo,
	thyu@master,tsong,xchzhang,xfma,xjwang,xli,xli@master,xqyao,xyyao@master,
	yaoli,ybliu,yfsun,youll,ytian,ytliu,zhangyou,zyju
    resources_default.nodes = 1
    resources_default.walltime = 336:00:00
    mtime = 1600756787
    resources_assigned.nodect = 7
    enabled = True
    started = True

Queue: Q_IB2
    queue_type = Execution
    total_jobs = 14
    state_count = Transit:0 Queued:9 Held:0 Waiting:0 Running:5 Exiting:0 Comp
	lete:0 
    acl_host_enable = True
    acl_hosts = master
    acl_user_enable = True
    acl_users = bwli,chbin,chengye,chenpan,chlwang,cosmoilc,dgwang,dingjian,dingwl,
	dlgao,dongkun,fhuo,fyan,fyang,haoli,huty,hyhe,jfwang,jhtong,jwchen,jyhe,jyqin,
	khzhang,klbi,kzzhang,lijin,liulei,liwei,lixl,longliu,lwang,mafei,mchwang,mgong,
	miwang,msi,qfli,qiancheng,rbbai,sguo,sswang,supersun,sxchen,tanxin,thyu,tsong,
	tzhang,wuzw,wzhsun,xchzhang,xhwu,xiexiaodong,xqyao,yanhw,yaoli,ybliu,yfsun,
	ylwang,youll,yqzhang,ytian,ytliu,yuke,ywli,yxia,yxyang,yyzhao,zdgan,zhangtao,
	zhangyou,zhuyx,zlwang,znzhong,zyju
    resources_default.nodes = 1
    resources_default.walltime = 9600:00:00
    mtime = 1600937530
    resources_assigned.nodect = 5
    enabled = True
    started = True