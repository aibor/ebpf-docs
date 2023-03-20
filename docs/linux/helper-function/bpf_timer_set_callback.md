# Helper function `bpf_timer_set_callback`

<!-- [FEATURE_TAG](bpf_timer_set_callback) -->
[:octicons-tag-24: v5.15](https://github.com/torvalds/linux/commit/b00628b1c7d595ae5b544e059c27b1f5828314b4)
<!-- [/FEATURE_TAG] -->

This helper sets the callback function for a [timer](../ebpf-concepts/timers.md).

## Definition
<!-- [HELPER_FUNC_DEF] -->
Configure the timer to call `callback_fn` static function.


**Returns**
0 on success.
`-EINVAL` if `timer` was not initialized with bpf_timer_init() earlier.
`-EPERM` if `timer` is in a map that doesn't have any user references.
The user space should either hold a file descriptor to a map with timers
or pin such map in bpffs. When map is unpinned or file descriptor is
closed all timers in the map will be cancelled and freed.

`#!c static long (*bpf_timer_set_callback)(struct bpf_timer *timer, void *callback_fn) = (void *) 170;`
<!-- [/HELPER_FUNC_DEF] -->

The function passed to `callback_fn` should have the following signature:

`#!c static int callback_fn(void *map, {map key type} *key, {map value type} *value)`

## Usage

### 

### Program types

This helper call can be used in the following program types:

<!-- TODO use generated list as soon as we can exclude functions from inherited groups -->
<!-- verifier.c excludes tracing programs from using timers -->
 * [BPF_PROG_TYPE_CGROUP_DEVICE](../program-type/BPF_PROG_TYPE_CGROUP_DEVICE.md)
 * [BPF_PROG_TYPE_CGROUP_SKB](../program-type/BPF_PROG_TYPE_CGROUP_SKB.md)
 * [BPF_PROG_TYPE_CGROUP_SOCK](../program-type/BPF_PROG_TYPE_CGROUP_SOCK.md)
 * [BPF_PROG_TYPE_CGROUP_SOCKOPT](../program-type/BPF_PROG_TYPE_CGROUP_SOCKOPT.md)
 * [BPF_PROG_TYPE_CGROUP_SOCK_ADDR](../program-type/BPF_PROG_TYPE_CGROUP_SOCK_ADDR.md)
 * [BPF_PROG_TYPE_CGROUP_SYSCTL](../program-type/BPF_PROG_TYPE_CGROUP_SYSCTL.md)
 * [BPF_PROG_TYPE_FLOW_DISSECTOR](../program-type/BPF_PROG_TYPE_FLOW_DISSECTOR.md)
 * [BPF_PROG_TYPE_LSM](../program-type/BPF_PROG_TYPE_LSM.md)
 * [BPF_PROG_TYPE_LWT_IN](../program-type/BPF_PROG_TYPE_LWT_IN.md)
 * [BPF_PROG_TYPE_LWT_OUT](../program-type/BPF_PROG_TYPE_LWT_OUT.md)
 * [BPF_PROG_TYPE_LWT_SEG6LOCAL](../program-type/BPF_PROG_TYPE_LWT_SEG6LOCAL.md)
 * [BPF_PROG_TYPE_LWT_XMIT](../program-type/BPF_PROG_TYPE_LWT_XMIT.md)
 * [BPF_PROG_TYPE_SCHED_ACT](../program-type/BPF_PROG_TYPE_SCHED_ACT.md)
 * [BPF_PROG_TYPE_SCHED_CLS](../program-type/BPF_PROG_TYPE_SCHED_CLS.md)
 * [BPF_PROG_TYPE_SK_LOOKUP](../program-type/BPF_PROG_TYPE_SK_LOOKUP.md)
 * [BPF_PROG_TYPE_SK_MSG](../program-type/BPF_PROG_TYPE_SK_MSG.md)
 * [BPF_PROG_TYPE_SK_REUSEPORT](../program-type/BPF_PROG_TYPE_SK_REUSEPORT.md)
 * [BPF_PROG_TYPE_SK_SKB](../program-type/BPF_PROG_TYPE_SK_SKB.md)
 * [BPF_PROG_TYPE_SOCKET_FILTER](../program-type/BPF_PROG_TYPE_SOCKET_FILTER.md)
 * [BPF_PROG_TYPE_SOCK_OPS](../program-type/BPF_PROG_TYPE_SOCK_OPS.md)
 * [BPF_PROG_TYPE_SYSCALL](../program-type/BPF_PROG_TYPE_SYSCALL.md)
 * [BPF_PROG_TYPE_TRACING](../program-type/BPF_PROG_TYPE_TRACING.md)
 * [BPF_PROG_TYPE_XDP](../program-type/BPF_PROG_TYPE_XDP.md)


### Example