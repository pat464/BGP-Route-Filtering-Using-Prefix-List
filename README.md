# BGP Route Filtering Using
===========================
This Lab contains 4 routers to illustrate BGP route filtering using prefix-lists.
AS 65100                      AS 65200                    AS 65300
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
R3 — Receives filtered routes, re-advertises to R4 with a different prefix-list (second filtering point)
R4 — Final verification point, receives only what survives both filters

IP Addressing Plan
===================
Link                     Subnet
R1–R2                    10.12.1.0/30 (R1:.1, R2:.2)

R2–R3                    10.23.1.0/30 (R2:.1, R3:.2)

R3–R4                    10.34.1.0/30 (R3:.1, R4:.2)
