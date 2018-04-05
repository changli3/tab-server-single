# AWS Template to set up a standalone Tableau server

## Notes Before Launch
* This is setting up https server, so you need to generate crt and key file and put where the machine can get (TableauServerCrt, TableauServerKey).
* You can provide the license key. Leave it as is if you need a trial.
* Replace all the values from your environment whereever applies.
* Some of the parameters are not listed here but you can find in the cloudformation template file.


## Usage

```
git clone https://github.com/changli3/tab-server-single.git

cd tab-server-single

aws cloudformation deploy --stack-name TableauSvr01 --parameter-overrides \
	ContentAdminPassword=admin123 \
	ContentAdminUser=admin \
	KeyPairName=TreaEBSLab \
	RegEmail=chang.li3@treasury.gov \
	RegFirstName=Chang \
	RegLastName=Li \
	AmiImageId=ami-e443379e \
	InstanceSubnet=subnet-2b976000 \
	InstanceSecurityGroup=sg-58e1fc3d \
    TableauServerLicenseKey= \
	TableauServerExe="https://downloads.tableau.com/esdalt/10.5.0/TableauServer-64bit-10-5-0.exe" \
    TableauServerCrt="https://s3.amazonaws.com/trlab-templates/tableau.crt" \
    TableauServerKey="https://s3.amazonaws.com/trlab-templates/tableau.key"  \
    --template-file tabsingle.tpl.json
```

