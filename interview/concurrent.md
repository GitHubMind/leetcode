# concurrent

#  what is the difference between unbuffered channel and buffered channel?

   unbuffered channel :  chan:= make(chan(int )) .It will block current the thread if  chan contains  any data Until the chan is cleared.
    
   in a buffered channel , it won't block as long as  channel is  not exhasted yet.
    make(chan(int),cap)

# what is Goroutine Leak

    + Don't clear out it in time.
    + Not closing the conext in time.
    + use GObal map or array ,but failing clear it in time.
    + channel blocking。
    + running is  an  infinite loop
