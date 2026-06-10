# EVPN/VXLAN Data Center Fabric

## Overview

This project demonstrates a small-scale EVPN/VXLAN data center fabric using:

- eBGP Underlay
- iBGP EVPN Overlay
- VXLAN Data Plane
- Leaf-Spine Architecture
- Layer 2 Extension Across Layer 3 Infrastructure

The goal is to illustrate how modern data centers separate transport (underlay) from tenant and service connectivity (overlay).

---

## Topology

### Control Plane

**Underlay**
- eBGP between Leaves and Spine
- Loopback reachability across the fabric
- ECMP-capable transport foundation

**Overlay**
- iBGP EVPN between VTEPs
- EVPN control-plane learning
- VXLAN encapsulation for tenant traffic

### Devices

| Device | Loopback |
|----------|----------|
| LEAF-1 | 1.1.1.1 |
| LEAF-2 | 2.2.2.2 |
| SPINE-1 | 3.3.3.3 |

Global BGP ASN: **65100**

---

## VLANs

### VLAN 10
- Server-Vlan10
- desktop-0vlan10

Subnet:
172.16.10.0/24

### VLAN 20
- desktop-1vlan20
- Server-Vlan20

Subnet:
172.16.20.0/24

---

## Architecture Rationale

This design follows a common modern data center model:

### eBGP Underlay

Benefits:

- Simple operational model
- Fast convergence
- Natural fit for leaf-spine topologies
- Clear routing boundaries
- Easy troubleshooting

The underlay acts as stable transport and provides reachability between VTEP loopbacks.

### iBGP EVPN Overlay

Benefits:

- Host mobility
- Scalable Layer 2 extension
- Multi-tenant segmentation
- Reduced flooding through control-plane learning
- Separation of tenant services from transport infrastructure

---

## Traffic Flow

1. End hosts connect to leaf switches.
2. Leaf switches operate as VXLAN Tunnel Endpoints (VTEPs).
3. EVPN distributes MAC/IP reachability information.
4. Traffic is encapsulated in VXLAN when crossing the routed fabric.
5. The eBGP underlay forwards VXLAN packets between VTEPs.

---

## Design Philosophy

The fabric demonstrates a common cloud and enterprise architecture pattern:

**Stable Underlay + Agile Overlay**

The underlay remains focused on IP transport while service provisioning, segmentation, and workload mobility are handled by EVPN/VXLAN.

This separation reduces operational complexity and allows network services to evolve independently of the transport fabric.

---

## Learning Objectives

This lab demonstrates:

- Leaf-spine design principles
- eBGP underlay deployment
- EVPN route exchange
- VXLAN encapsulation
- Layer 2 extension across Layer 3 boundaries
- Modern data center architecture concepts

---

## Author Notes

This topology was built as a learning and demonstration environment to explore the interaction between:

- eBGP underlays
- iBGP EVPN overlays
- VXLAN transport
- Data center segmentation and scalability

## 📧 Contact

- **Author**: Patrick Ukponu
- Network Engineer|CCNP Enterprise|Cyber Security Specialist|
- **LinkedIn**: https://www.linkedin.com/in/patrick-u-78a001176/
- **Email**: pat.ukponu@gmail.com