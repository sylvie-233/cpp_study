# Linux C++基础

Sylvie233的Linux C++学习~~~

> Author: Sylvie233
>
> Date: 2022/11/10
>
> Update: 2022/11/11
>
> Point: linux系统编程P15

[TOC]

## Linux C++基础

### 静态库

文件：`.a`

归档文件：打包.o文件

ar工具：生成静态库





### 共享库

文件：`.so`



动态库在编译可执行文件时，可执行文件中只记录符号和对应的动态库版本信息

运行时动态加载共享库（共享库在内存中只存在一份）



real name、so name、link name

主版本号、次版本号

链接时只关联动态库的主版本号



ld链接器

配置文件：`/etc/ld.so.conf`

```
添加动态库查找路径
```





ldd命令：查看程序依赖的动态库

```
linux-gate.so.1 => (0xb77e0000)
libc.so.6 => /lib/i386-linux-gnu/libc.so.6(0xb7622000)
...
/lib/ld-linux.so.2(0xb7731000)
```



### 文件I/O

FILE指针

inode、f_pos、buffer

inode文件描述符：文件关联的磁盘中的block块

每个FILE指针都对应一个缓存区



libc库中的I/O函数都带有缓存区（c标准缓存区），write写入内核缓存区、守护进程定时刷新内核缓存区



pcb中包含进程关联的文件列表

最大打开文件个数：1024

>ulimit -a: 查看open files的限制
>
>ulimit -n: 修改最大文件个数

进程默认关联的3个标准文件流

```
STDIN_FILENO 0
STDOUT_FILENO 1
STDERR_FILENO 2
```





阻塞与非阻塞I/O

read终端输入默认阻塞







### 文件系统





### 进程控制

#### PCB

进程控制块

task_struct结构体

```c++
struct task_struct {
#ifdef CONFIG_THREAD_INFO_IN_TASK
  struct thread_info    thread_info;
#endif
  volatile long     state;
  randomized_struct_fields_start
  void        *stack;
  refcount_t      usage;
  unsigned int      flags;
  unsigned int      ptrace;
#ifdef CONFIG_SMP
  struct llist_node   wake_entry;
  int       on_cpu;
#ifdef CONFIG_THREAD_INFO_IN_TASK
  unsigned int      cpu;
#endif
  unsigned int      wakee_flips;
  unsigned long     wakee_flip_decay_ts;
  struct task_struct    *last_wakee;
  int       recent_used_cpu;
  int       wake_cpu;
#endif
  int       on_rq;
  int       prio;
  int       static_prio;
  int       normal_prio;
  unsigned int      rt_priority;
  const struct sched_class  *sched_class;
  struct sched_entity   se;
  struct sched_rt_entity    rt;
#ifdef CONFIG_CGROUP_SCHED
  struct task_group   *sched_task_group;
#endif
  struct sched_dl_entity    dl;
#ifdef CONFIG_UCLAMP_TASK
  struct uclamp_se    uclamp_req[UCLAMP_CNT];
  struct uclamp_se    uclamp[UCLAMP_CNT];
#endif
#ifdef CONFIG_PREEMPT_NOTIFIERS
  struct hlist_head   preempt_notifiers;
#endif
#ifdef CONFIG_BLK_DEV_IO_TRACE
  unsigned int      btrace_seq;
#endif
  unsigned int      policy;
  int       nr_cpus_allowed;
  const cpumask_t     *cpus_ptr;
  cpumask_t     cpus_mask;
#ifdef CONFIG_PREEMPT_RCU
  int       rcu_read_lock_nesting;
  union rcu_special   rcu_read_unlock_special;
  struct list_head    rcu_node_entry;
  struct rcu_node     *rcu_blocked_node;
#endif
#ifdef CONFIG_TASKS_RCU
  unsigned long     rcu_tasks_nvcsw;
  u8        rcu_tasks_holdout;
  u8        rcu_tasks_idx;
  int       rcu_tasks_idle_cpu;
  struct list_head    rcu_tasks_holdout_list;
#endif
  struct sched_info   sched_info;
  struct list_head    tasks;
#ifdef CONFIG_SMP
  struct plist_node   pushable_tasks;
  struct rb_node      pushable_dl_tasks;
#endif
  struct mm_struct    *mm;
  struct mm_struct    *active_mm;
  struct vmacache     vmacache;
#ifdef SPLIT_RSS_COUNTING
  struct task_rss_stat    rss_stat;
#endif
  int       exit_state;
  int       exit_code;
  int       exit_signal;
  int       pdeath_signal;
  unsigned long     jobctl;
  unsigned int      personality;
  unsigned      sched_reset_on_fork:1;
  unsigned      sched_contributes_to_load:1;
  unsigned      sched_migrated:1;
  unsigned      sched_remote_wakeup:1;
#ifdef CONFIG_PSI
  unsigned      sched_psi_wake_requeue:1;
#endif
  unsigned      :0;
  unsigned      in_execve:1;
  unsigned      in_iowait:1;
#ifndef TIF_RESTORE_SIGMASK
  unsigned      restore_sigmask:1;
#endif
#ifdef CONFIG_MEMCG
  unsigned      in_user_fault:1;
#endif
#ifdef CONFIG_COMPAT_BRK
  unsigned      brk_randomized:1;
#endif
#ifdef CONFIG_CGROUPS
  unsigned      no_cgroup_migration:1;
  unsigned      frozen:1;
#endif
#ifdef CONFIG_BLK_CGROUP
  unsigned      use_memdelay:1;
#endif
  unsigned long     atomic_flags;
  struct restart_block    restart_block;
  pid_t       pid;
  pid_t       tgid;
#ifdef CONFIG_STACKPROTECTOR
  unsigned long     stack_canary;
#endif
  struct task_struct __rcu  *real_parent;
  struct task_struct __rcu  *parent;
  struct list_head    children;
  struct list_head    sibling;
  struct task_struct    *group_leader;
  struct list_head    ptraced;
  struct list_head    ptrace_entry;
  struct pid      *thread_pid;
  struct hlist_node   pid_links[PIDTYPE_MAX];
  struct list_head    thread_group;
  struct list_head    thread_node;
  struct completion   *vfork_done;
  int __user      *set_child_tid;
  int __user      *clear_child_tid;
  u64       utime;
  u64       stime;
#ifdef CONFIG_ARCH_HAS_SCALED_CPUTIME
  u64       utimescaled;
  u64       stimescaled;
#endif
  u64       gtime;
  struct prev_cputime   prev_cputime;
#ifdef CONFIG_VIRT_CPU_ACCOUNTING_GEN
  struct vtime      vtime;
#endif
#ifdef CONFIG_NO_HZ_FULL
  atomic_t      tick_dep_mask;
#endif
  unsigned long     nvcsw;
  unsigned long     nivcsw;
  u64       start_time;
  u64       start_boottime;
  unsigned long     min_flt;
  unsigned long     maj_flt;
  struct posix_cputimers    posix_cputimers;
  const struct cred __rcu   *real_cred;
  const struct cred __rcu   *cred;
#ifdef CONFIG_KEYS
  struct key      *cached_requested_key;
#endif
  char        comm[TASK_COMM_LEN];
  struct nameidata    *nameidata;
#ifdef CONFIG_SYSVIPC
  struct sysv_sem     sysvsem;
  struct sysv_shm     sysvshm;
#endif
#ifdef CONFIG_DETECT_HUNG_TASK
  unsigned long     last_switch_count;
  unsigned long     last_switch_time;
#endif
  struct fs_struct    *fs;
  struct files_struct   *files;
  struct nsproxy      *nsproxy;
  struct signal_struct    *signal;
  struct sighand_struct __rcu   *sighand;
  sigset_t      blocked;
  sigset_t      real_blocked;
  sigset_t      saved_sigmask;
  struct sigpending   pending;
  unsigned long     sas_ss_sp;
  size_t        sas_ss_size;
  unsigned int      sas_ss_flags;
  struct callback_head    *task_works;
#ifdef CONFIG_AUDIT
#ifdef CONFIG_AUDITSYSCALL
  struct audit_context    *audit_context;
#endif
  kuid_t        loginuid;
  unsigned int      sessionid;
#endif
  struct seccomp      seccomp;
  u64       parent_exec_id;
  u64       self_exec_id;
  spinlock_t      alloc_lock;
  raw_spinlock_t      pi_lock;
  struct wake_q_node    wake_q;
#ifdef CONFIG_RT_MUTEXES
  struct rb_root_cached   pi_waiters;
  struct task_struct    *pi_top_task;
  struct rt_mutex_waiter    *pi_blocked_on;
#endif
#ifdef CONFIG_DEBUG_MUTEXES
  struct mutex_waiter   *blocked_on;
#endif
#ifdef CONFIG_DEBUG_ATOMIC_SLEEP
  int       non_block_count;
#endif
#ifdef CONFIG_TRACE_IRQFLAGS
  unsigned int      irq_events;
  unsigned long     hardirq_enable_ip;
  unsigned long     hardirq_disable_ip;
  unsigned int      hardirq_enable_event;
  unsigned int      hardirq_disable_event;
  int       hardirqs_enabled;
  int       hardirq_context;
  unsigned long     softirq_disable_ip;
  unsigned long     softirq_enable_ip;
  unsigned int      softirq_disable_event;
  unsigned int      softirq_enable_event;
  int       softirqs_enabled;
  int       softirq_context;
#endif
#ifdef CONFIG_LOCKDEP
# define MAX_LOCK_DEPTH     48UL
  u64       curr_chain_key;
  int       lockdep_depth;
  unsigned int      lockdep_recursion;
  struct held_lock    held_locks[MAX_LOCK_DEPTH];
#endif
#ifdef CONFIG_UBSAN
  unsigned int      in_ubsan;
#endifW
  void        *journal_info;
  struct bio_list     *bio_list;
#ifdef CONFIG_BLOCK
  struct blk_plug     *plug;
#endif
  struct reclaim_state    *reclaim_state;
  struct backing_dev_info   *backing_dev_info;
  struct io_context   *io_context;
#ifdef CONFIG_COMPACTION
  struct capture_control    *capture_control;
#endif
  unsigned long     ptrace_message;
  kernel_siginfo_t    *last_siginfo;
  struct task_io_accounting ioac;
#ifdef CONFIG_PSI
  unsigned int      psi_flags;
#endif
#ifdef CONFIG_TASK_XACCT
  u64       acct_rss_mem1;
  u64       acct_vm_mem1;
  u64       acct_timexpd;
#endif
#ifdef CONFIG_CPUSETS
  nodemask_t      mems_allowed;
  seqcount_t      mems_allowed_seq;
  int       cpuset_mem_spread_rotor;
  int       cpuset_slab_spread_rotor;
#endif
#ifdef CONFIG_CGROUPS
  struct css_set __rcu    *cgroups;
  struct list_head    cg_list;
#endif
#ifdef CONFIG_X86_CPU_RESCTRL
  u32       closid;
  u32       rmid;
#endif
#ifdef CONFIG_FUTEX
  struct robust_list_head __user  *robust_list;
#ifdef CONFIG_COMPAT
  struct compat_robust_list_head __user *compat_robust_list;
#endif
  struct list_head    pi_state_list;
  struct futex_pi_state   *pi_state_cache;
  struct mutex      futex_exit_mutex;
  unsigned int      futex_state;
#endif
#ifdef CONFIG_PERF_EVENTS
  struct perf_event_context *perf_event_ctxp[perf_nr_task_contexts];
  struct mutex      perf_event_mutex;
  struct list_head    perf_event_list;
#endif
#ifdef CONFIG_DEBUG_PREEMPT
  unsigned long     preempt_disable_ip;
#endif
#ifdef CONFIG_NUMA
  struct mempolicy    *mempolicy;
  short       il_prev;
  short       pref_node_fork;
#endif
#ifdef CONFIG_NUMA_BALANCING
  int       numa_scan_seq;
  unsigned int      numa_scan_period;
  unsigned int      numa_scan_period_max;
  int       numa_preferred_nid;
  unsigned long     numa_migrate_retry;
  u64       node_stamp;
  u64       last_task_numa_placement;
  u64       last_sum_exec_runtime;
  struct callback_head    numa_work;
  struct numa_group __rcu   *numa_group;
  unsigned long     *numa_faults;
  unsigned long     total_numa_faults;
  unsigned long     numa_faults_locality[3];
  unsigned long     numa_pages_migrated;
#endif
#ifdef CONFIG_RSEQ
  struct rseq __user *rseq;
  u32 rseq_sig;
  unsigned long rseq_event_mask;
#endif
  struct tlbflush_unmap_batch tlb_ubc;
  union {
    refcount_t    rcu_users;
    struct rcu_head   rcu;
  };
  struct pipe_inode_info    *splice_pipe;
  struct page_frag    task_frag;
#ifdef CONFIG_TASK_DELAY_ACCT
  struct task_delay_info    *delays;
#endif
#ifdef CONFIG_FAULT_INJECTION
  int       make_it_fail;
  unsigned int      fail_nth;
#endif
  int       nr_dirtied;
  int       nr_dirtied_pause;
  unsigned long     dirty_paused_when;
#ifdef CONFIG_LATENCYTOP
  int       latency_record_count;
  struct latency_record   latency_record[LT_SAVECOUNT];
#endif
  u64       timer_slack_ns;
  u64       default_timer_slack_ns;
#ifdef CONFIG_KASAN
  unsigned int      kasan_depth;
#endif
#ifdef CONFIG_FUNCTION_GRAPH_TRACER
  int       curr_ret_stack;
  int       curr_ret_depth;
  struct ftrace_ret_stack   *ret_stack;
  unsigned long long    ftrace_timestamp;
  atomic_t      trace_overrun;
  atomic_t      tracing_graph_pause;
#endif
#ifdef CONFIG_TRACING
  unsigned long     trace;
  unsigned long     trace_recursion;
#endif
#ifdef CONFIG_KCOV
  unsigned int      kcov_mode;
  unsigned int      kcov_size;
  void        *kcov_area;
  struct kcov     *kcov;
  u64       kcov_handle;
  int       kcov_sequence;
#endif
#ifdef CONFIG_MEMCG
  struct mem_cgroup   *memcg_in_oom;
  gfp_t       memcg_oom_gfp_mask;
  int       memcg_oom_order;
  unsigned int      memcg_nr_pages_over_high;
  struct mem_cgroup   *active_memcg;
#endif
#ifdef CONFIG_BLK_CGROUP
  struct request_queue    *throttle_queue;
#endif
#ifdef CONFIG_UPROBES
  struct uprobe_task    *utask;
#endif
#if defined(CONFIG_BCACHE) || defined(CONFIG_BCACHE_MODULE)
  unsigned int      sequential_io;
  unsigned int      sequential_io_avg;
#endif
#ifdef CONFIG_DEBUG_ATOMIC_SLEEP
  unsigned long     task_state_change;
#endif
  int       pagefault_disabled;
#ifdef CONFIG_MMU
  struct task_struct    *oom_reaper_list;
#endif
#ifdef CONFIG_VMAP_STACK
  struct vm_struct    *stack_vm_area;
#endif
#ifdef CONFIG_THREAD_INFO_IN_TASK
  refcount_t      stack_refcount;
#endif
#ifdef CONFIG_LIVEPATCH
  int patch_state;
#endif
#ifdef CONFIG_SECURITY
  void        *security;
#endif
#ifdef CONFIG_GCC_PLUGIN_STACKLEAK
  unsigned long     lowest_stack;
  unsigned long     prev_lowest_stack;
#endif
  randomized_struct_fields_end
  struct thread_struct    thread;
};
```

简化pcb

```c++
struct task_struct {
    pid_t pid;
    struct files_struct *files;
};
```









### 进程通信



#### 管道

#### 信号

#### IPC



### 网络编程



### 线程



### I/O复用



### 异步I/O













## 常用API

### <fcntl.h>

### <sys/stat.h>

### <sys/types.h>

### <unistd.h>



### close

```
#include <unistd.h>

int close(int fd)
```



### creat

```
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

int creat(const char *pathname, mode_t mode)
```



### open

```
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

int open(const char *pathname, int flags);
int open(const char *pathname, int flags, mode_t mode)
	flags: 标志
		O_CREAT: 创建
		O_RDWR: 可读可写
		O_APPEND: 追加
		O_WRONLY: 只写
		O_RDONLY: 只读
		O_TRUNC: 截断
		O_EXCL: 已存在则出错返回
		O_NONBLOCK: 非阻塞I/O
		
	mode: 权限
		0644
	
返回值:
	-1: 打开失败
	fd: 文件描述符（进程文件描述符表中未使用的最小的值）
```



### read

```
#include <unistd.h>

ssize_t read(int fd, void *buf, size_t count)

返回值:
	-1: 异常
	0: 读取到文件末尾
	n: 读取的字节个数
```



### umask

```
#include <sys/types.h>
#include <sys/stat.h>

mode_t umask(mode_t mask)
```



### write



```
#include <unistd.h> 

ssize_t write(int fd, const void *buf, size_t count)
```

