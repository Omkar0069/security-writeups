# Client-Server Basics

## Overview

This room explains basics of Virtualization.

## What I Learned

Virtualization enables difference computer services to run underneath same physical hardware.
A virtualization layer, called a hypervisor, was introduced to act as a referee between lab machines and allow each virtual computer to behave independently, like a physical computer.
Hypervisors have two main types of implementation, each of which is used for specific scenarios, from home labs to large data centers:

    Type 1 hypervisors run directly on the physical hardware, making them fast, efficient, and ideal for servers and professional environments.
    Type 2 hypervisors run within an existing operating system, making them easier to install and ideal for learning, testing, or small setups.

The easiest way to deploy containers in a VM is using Docker.
Docker is an open-source software platform that simplifies the process of building, deploying, and running applications using containerization.

## Exercises

### Exercise 1 — [Virtualization Overview]

**Q1.** What does virtualization enable multiple applications to share?
**Answer:** Physical Server

**Q2.** What is the name of the software that manages the resources for each lab machine?
**Answer:** Hypervisor

### Exercise 2 — [Managing Virtual Machines]

**Q1.** Suppose a user wants to deploy a study lab on their machine to practice some exercises for a cyber security certification. Which type of hypervisor will they use?
**Answer:** Type 2

**Q2.** Suppose a company wants to host multiple small applications in the same lab machine. What should they use?
**Answer:** Containers

### Exercise 3 — [Virtualization Components]

**Q1.** What is the name of the lab machine that has been running for the longest time?
**Answer:** Monitoring-SYS

**Q2.** What is the name of the lab machine that is using the biggest amount of memory?
**Answer:** DB-Cluster-01

**Q3.** How many VMs are in the running state after you solved the issue on `Mail-SERVER`?
**Answer:** 8
**Q4.** What is the name of the physical machine that is hosting most of the VMs?
**Answer:** HV-Prod-02

## Key Takeaways

Virtualization: Enables a single physical computer to act like multiple separate computers.
Hypervisor: The “manager” software that makes and runs the virtual computers.
Lab Machine (): A whole virtual computer inside the real one, with its own system.
Container: A small, isolated box for one app that shares the same system as the host.
Container Images: A pre-packed recipe/template used to create containers.
Network Ports: Special numbered entry points that apps use to talk over the network.

## Notes

VM: needs a hypervisor.
Container: doesn't inherently need a VM.
Container on Linux: can run directly on the host kernel.