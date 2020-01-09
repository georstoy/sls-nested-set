# CloudFormation Set-up steps:
 - VPC
   - region: eu-central-1 
   - subnets:
     - Tag: public
       -  CIDR: 10.0.0.0/16 (for ApiGateway)
       -  availability for each zone
     - Tag: private
       - CIDR: 10.1.0.0/16 (for DB instance)
       - availability:  for each zone

   - security groups:
     - public
       - inbound rules:
         - Type: Http source: IP
         - Type: SSH source: IP
     - private
       - inbound rules:
         - Type: Mysql/Aurora
         - source: ApiGateway

 - RDS
   - DB Subnet Group

# TODO
 - Add ApiGateway to the security group ?

# Reference materials
 - [Tutorial: Create an Amazon VPC for Use with a DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Tutorials.WebServerDB.CreateVPC.html#CHAP_Tutorials.WebServerDB.CreateVPC.SecurityGroupDB)