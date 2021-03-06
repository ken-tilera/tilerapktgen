Tilera packet generator
=======================

This program generate UDP packets and send them at line rate through some specified interfaces using mPipe. It counts the number of packets received too.

It was made for TileEncore Gx36 but should work on other Tilera devices.

It counts the number of packets sent and received for a range of packet sizes and displays some statistics like the throughput in lines of format :

  prefix_text packet_size time_elapsed packet_sent packet_received transmit_rate receive_rate transmit_speed receive_speed wire_transmit_speed wire_receveive_speed loss_rate

If you use it as a generator in a loop, the difference between packet sent and received will include a very small error as we count the number of packets while still sending and receiving to capture the speed only at full rate. Therefore, do not use it to test if the tested equipments side loose a very small number of packets.

The destination MAC address and IP address can be randomized to be able to use load balance (RSS, ...) on the receive side.

This program is given without license but is based on and include parts of codes from the Tilera MDE samples. Please keep my name (Tom Barbette) and University of Liege if you re-use the code.

###Typical compile command

tile-gcc --std=gnu99 -o tester udp.c app.c -lpthread -lgxio -ltmc


###Typical usage

./tester --link xgbe1,xgbe2,xgbe3,xgbe4 -w 12

12 threads are sufficient for 4*linerate 

##License

This software is made by Tom Barbette from University of Liege and is not a product of Tilera Corporation but include code taken from Tilera MDE samples. You may copy, distribute or modify this software including for commercial purpose but you're kindly asked to keep the name of the author and any further contributor and its/their institution(s).
