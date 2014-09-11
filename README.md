Yahoo! Cloud System Benchmark (YCSB)
====================================

This is a modified YCSB for benchmarking Cassandra counters.


Getting Started
---------------

1. Download the latest release of YCSB:

    git clone git://github.com/wentingwang/YCSB.git
    cd YCSB
    mvn clean package

2. Set up a cassandra database to benchmark. Use cassandra-cli to do these commands:

   create keyspace usertable;
   use usertable;
   create column family data;
   create column family counter_table with default_validation_class=CounterColumnType and replicate_on_write=true;

3. Run YCSB command. 

    ./bin/ycsb run cassandra-10 -s -P workloads/workloadcounter -p hosts="localhost" -p cassandra.countnum=2 -p cassandra.countincrement=1

   See https://github.com/brianfrankcooper/YCSB/wiki/Running-a-Workload
   for a detailed documentation on how to run a workload.

   See https://github.com/brianfrankcooper/YCSB/wiki/Core-Properties for 
   the list of available workload properties.
