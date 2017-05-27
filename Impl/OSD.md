OSD implementation
=====

The source code of OSD module is at src/osd. The goal for OSD is mainly for 
PG management, IO schedule, replication management.

# OSD class

OSD implements Dispatcher. It needs to interact with CLIENT, MONITOR, PEERs. 
The OSD instance keeps track of all these connections. `OSD::init` will 
initialize the OSD and OSDService

    cluster_messager 
    client_messager 
    hb_client_front
    hb_client_back
    fb_front_serverm
    fb_back_serverm
    objecter_messager
    monc                      //Monclient

## Interaction between Monitor

MonClient: monc--> client_messager(Messager)

SafeTimer: calls callback function when time clapsed. Will try to acquire
a lock before call the callback. Inside the timer, there is a working 
thread remeber when the timer is dued and calls the callback. The logic 
lies in `SafeTimer::timer_thread`. `SafeTimer::init` will create a timer
thread and start executing `SafeTimer::timer_thread`.

    tick_timer ---->(locked by) osd_lock
    tick_timer_without_osd_lock ---->(locked by) tick_timer_lock

# OSDService

    recovery_request_timer

# Object

    +---------------------------------------------+
    |   byte data   | xattrs | omap_header | omap |
    +---------------------------------------------+

# Transaction

    Atomic
    Concurrency Control
    Rollback
    Serialize


