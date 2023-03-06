##PREREQUISITES
*KeyPair
####[Follow these instructions to create a key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/create-key-pairs.html)
##How to run the template

####Step 1: Create VPC
    * 1.Log in to your AWS account. 
    * 2. Search Cloudformation.   
    * 3. Navigate to Cloudformation homepage
    * 4. Click on 'Create Stack'
    * 5. Under 'Specify template', choose 'upload a template file' radio button and choose file to upload.
    * 6. Select the vpc.yaml file and click next
    * 7. Enter Stack name and click next
    * 8. On 'Configure stack options' leave as default and click next
    * 9. Review and click Submit. Wait for 'CREATE_COMPLETE' to dispay on the left of the screen under the stack name.

####Step 2: Create Internet Gateway
    * 1. On the right side, click on create stack and choose 'with new resources(standard)' on the dropdown menu that appears.
    * 2. Repeat instruction 5 & 6 in Step 1. Choose igw.yaml file. Under parameters,click on the dropdown menu and choose myVPC
    * 3. Leave everything else as default and Submit. Wait for resources to complete creating. Navigate to VPC-Internet Gateways and note down in a text editor the ID of the igw attached to myVPC.

####Step 3: Create Subnets and Associations
    * 1. Repeat Instructions 1 & 2 in Step 2. Choose subnetassociations.yaml file. Under Parameters paste in the igw value and select myVPC. Click Next.
    * 2. Leave everything else as default and click Submit.
    Navigate to VPC Subnets and note down in a text editor the values for the two subnets you just created(Public Subnet 1 and Public Subnet 2)

####Step 4: Create Target Group, Security Group, Load Balancer and AutoScaling Group.
    * 1. Repeat Instructions 1 & 2 in Step 2 above. Choose targetGroup.yaml file. Under parameters choose your KeyPair, Enter the values for the subnets noted above then choose myVPC.
    * 2. Leave everything else as default and click Submit
    When the stack creation is complete, navigate to EC2 - instances. Wait for the message '2/2 checks passed' to display under Status Check. Select one of the instances and click on 'Public IPv4 address' on the Details Tab that appears at the bottom. Apache Homepage displays in a new tab.