# DMVPN Phase 2 with EIGRP

Hub-and-spoke DMVPN over multipoint GRE with NHRP, running EIGRP across the tunnel so that spokes can build direct spoke-to-spoke tunnels.

- `configs/r3.cfg`, `configs/r4.cfg`: spoke routers (`tunnel mode gre multipoint`, NHRP mapping to the hub, `ip nhrp nhs`, network ID, EIGRP).
- `configs/r5.cfg` to `r7.cfg`: LAN routers behind the sites, advertising their networks into EIGRP.
- For Phase 2, EIGRP split-horizon and next-hop-self were turned off on the hub tunnel, so spokes learn each other's routes with the real next hop.
- `verification/`: `show dmvpn` and `show ip nhrp`, `show ip route eigrp` on R5 to R7, and a traceroute showing traffic going directly between spokes.
- `captures/nhrp-registration.pcapng`: spokes registering their tunnel-to-public address mapping with the hub (next hop server).

---
Lab work from my Master of Engineering in Internetworking, Dalhousie University (2024 to 2026). Course handouts and graded answer sheets are not included.

Author: Vikramjeet Singh, [LinkedIn](https://www.linkedin.com/in/vikramjeet-singh-75b7a2183)
