# Implementation of TINIEE
This is the implementation of "TINIEE: Traffic-Aware Adaptive In-Network Intelligence via Early-Exit Strategy" on the Tofino switch with P4 language.

## Tofino Instructions
Our code is available in SDE 9.13.3.

1. Download the repository to the local.

2. Compile P4 program
   ```
   ./build_tofino.sh [abs_path for the cloned directory]/TINIEE/tofino/p4src/tiniee_first.p4 tiniee_first
   ```
   
3. Run switch model
   ```
   $SDE/run_tofino_model.sh -p tiniee_first
   ```
   
4. Run switch driver
   ```
   $SDE/run_switchd.sh -p tiniee_first
   bfshell> bfrt_python [abs_path for the cloned directory]/tiniee/rule/bfrt_rule_tiniee_first.py
   ```
   
5. Packet generation
   ```
   [Sender] python3 [abs_path for the cloned directory]/tiniee/tofino/packets/send.py
   [Receiver 1] python3 [abs_path for the cloned directory]/tiniee/tofino/packets/receive_process.py
   [Receiver 2] python3 [abs_path for the cloned directory]/tiniee/tofino/packets/receive_exit.py
   ```
