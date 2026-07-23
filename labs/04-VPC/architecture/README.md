# Architecture

## Overview

This architecture demonstrates a basic AWS network composed of a custom VPC with one public subnet and one private subnet.

The public subnet hosts an Amazon EC2 instance running Apache Web Server. Internet access is provided through an Internet Gateway and a Route Table associated with the public subnet.

## Components

- Amazon VPC
- Public Subnet
- Private Subnet
- Internet Gateway
- Route Table
- Security Group
- Amazon EC2
- Apache HTTP Server

## Diagram

See:

export/lab04-vpc-architecture.png

## Network Flow

Internet

↓

Internet Gateway

↓

Public Route Table

↓

Public Subnet

↓

Amazon EC2

↓

Apache Web Server