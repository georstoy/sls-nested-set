# CloudFormation Set-up steps:
 - VPC
   - region: eu-central-1 
   - subnets:
     - Tag: public
       -  CIDR: 10.0.0-2.0/24 (for ApiGateway)
       -  availability for each zone
     - Tag: private //TODO
       - CIDR: 10.0.100-102.0/24 (for DB instance)
       - availability:  for each zone

 - Route Table:
 - Internet Gateway:
 - Endpoint (for internal services) NOT NEEDED

 - Elastic IP: 3.126.12.254 // What this is needed for??

 - Security groups:
   - public
     - inbound rules:
       - Type: SSH source: my IPs
     - AutoAssign Public IPs 

   - private
     - inbound rules:
       - Type: Mysql/Aurora
       - source: ApiGateway

// I DON'T NEED EC2 TO HAVE A WORKING RDS INSTANCE
// - EC2 Requirements
//   - EFS filesystem
//   - KeyPair
//
// - EC2 instance Ubuntu 18.04
//   - Private IP:
//   - Public IP: // MUST HAVE TO BE ACCESSIBLE

 - RDS
   - DB Subnet Group

# TODO
 - Add ApiGateway to the security group ?

# Reference materials
 - [Tutorial: Create an Amazon VPC for Use with a DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Tutorials.WebServerDB.CreateVPC.html#CHAP_Tutorials.WebServerDB.CreateVPC.SecurityGroupDB)