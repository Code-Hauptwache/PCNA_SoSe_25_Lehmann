# VLAN Lab Exercise 3: Experimental Plan for IEEE 802.1Q Network Segmentation

## What is VLAN?

A **Virtual Local Area Network (VLAN)** is a technology that allows you to create multiple logical networks within a single physical network infrastructure. VLANs segment a network at Layer 2 (Data Link Layer), creating separate broadcast domains. This means devices in different VLANs cannot communicate directly, even if connected to the same physical switch, unless routing is configured between them.

## Network Topology Identification

![alt text](image.png)
***Note**: The interfaces in the Lab shall be: eth0 = enp1s0f1 and eth2 = enp1s0f0*

## VLAN Implementation Methods

| Feature               | Tagged (802.1Q)                                                                                      | Untagged (Access)                                                      |
|-----------------------|------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **Frame Format**      | Inserts a 4-byte 802.1Q header carrying the VLAN ID and priority bits.                               | Sends/receives plain Ethernet frames with no VLAN header.              |
| **Typical Use Case**  | Trunk links (Switch↔Switch, Switch↔Router) carrying many VLANs (e.g. 10, 20, 30) over one cable.     | Access links (Switch↔Host) where each port belongs to exactly one VLAN. |
| **Ingress Behavior**  | Reads the VLAN tag on each incoming frame and forwards into the corresponding VLAN.                 | Assigns every incoming frame to the port’s PVID (no tag expected).      |
| **Egress Behavior**   | Adds the 802.1Q header with the VLAN ID before sending the frame.                                    | Strips any VLAN header and sends a “normal” Ethernet frame.             |
| **Advantages**        | + Consolidates multiple VLANs on a single link<br>+ Essential for larger, multi-switch networks     | + Simple for end-hosts (no VLAN config required)<br>+ Zero tagging overhead |
| **Trade-offs**        | – Slight overhead (4 bytes/frame)<br>– Requires VLAN-aware devices¹ and configuration                | – One cable or port per VLAN needed<br>– Not suitable for multi-VLAN links |

¹ **VLAN-aware devices**: Network devices (hosts, switches, routers) that understand and can process 802.1Q VLAN tags. These devices must have drivers/firmware supporting VLAN tagging and the ability to create virtual interfaces (e.g., eth0.10 for VLAN 10).

## Experimental Setup and Testing

### Step 1: Initial Setup
• **Select Router 1 computer**: Choose the Linux machine connected to external Router 2
• **Verify connectivity**: Check enp1s0f1 is connected to Router 2, enp1s0f0 available for switch
• **Enable IPv6**: Configure IPv6 on enp1s0f1 to get Internet access
  ```bash
  // TODO: Commands needed to configure IPv6 for the network
  ```

### Step 2: Choose Implementation Method

// TODO: Next steps