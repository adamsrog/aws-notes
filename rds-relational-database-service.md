# Relational Database Service (RDS)

AWS re:Invent 2015 | (DAT304) Amazon RDS for MySQL: Best Practices - https://www.youtube.com/watch?v=eHg8LD5KNC0

## What's New
* Encryption at rest using AWS Key Management Service
* Max DB size is now 6 TB (was 1 TB)
* Simplified Reserved Instance pricing
* HIPAA, BAA, and FedRamp compliance
* AWS Database Migration Service




AWS Summit Series 2016 | Chicago - Deep Dive on Amazon Relational Database Service - https://www.youtube.com/watch?v=9-7azhB27So

## Trade-offs with Managed Service
* No access to database host OS
* No functions that rely on configuration of the host OS

## Security
* Launches in to a VPC.
* Security groups act as a firewall for the database.
* Compliance with many standards: HIPAA, ISO, Gov.UK, FedRamp (more)
* SSL - database traffic encryption
* At-rest encryption: storage, backups, replicas, snapshots
