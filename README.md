#This Lab focuses entirely on BGP route filtering using prefix-lists matching with Grater than or equal to ( ge: >=) and Less than or equal to, (le:<=) in BGP.
#Prefix-lists provides the flexibility to match multiple networks with specific prefix length with one statement.

   AS 65100                      AS 65200                   AS 65300
  +--------+                    +--------+                  +--------+
  |   R1   |------------------- |   R2   |------------------|   R3   |
  +--------+    10.12.1.0/30    +--------+   10.23.1.0/30   +--------+
                                                                  |
                                                                  | 10.34.1.0/30
                                                                  |
                                                             +--------+
                                                             |   R4   |
                                                             +--------+
                                                              AS 65400
Role of each router:
R1 — Originates multiple prefixes of varying lengths.
R2 — Applies prefix-list filtering toward R3 (the core of this lab)
#This uses high-order-bit-pattern (the network address to match against - 172.16.0.0) and high-order-bit-count (bits to match exactly - for instance /24 in 172.16.0.0/24)
R3 — Receives filtered routes, re-advertises to R4 with a different prefix-list (second filtering point)
R4 — Final verification point, receives only what survives both filters

IP Addressing Plan
===================
Link                Subnet
R1–R2               10.12.1.0/30 (R1:.1, R2:.2)
R2–R3               10.23.1.0/30 (R2:.1, R3:.2)
R3–R4               10.34.1.0/30 (R3:.1, R4:.2)
