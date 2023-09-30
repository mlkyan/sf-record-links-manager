# Useful SFDX commands


#### 1) Login into the org

Prod/Dev:
```
sf org login web -d -a orgAlias
```

Sandbox:
```
sf org login web -d -r https://test.salesforce.com -a orgAlias
```


#### 2) Set default dev-hub or scratch org in the current folder or global (add key: --global)


```
sf config set target-org=orgAlias
```


#### 3) Create scratch org:

````
sf org create scratch -f config/project-scratch-def.json -d 30 -s -a scratchOrgAlias
````


#### 4) Open scratch org (for not default use: -o / -u orgAlias)
```
sf org open
```


#### 5) Retrieve metadata:
```
sf project retrieve start -x assets/package.xml -p unpackaged -o orgAlias -w 10
```

#### 6) Convert (metadata > dx format):
```
sf project convert mdapi --rootdir retrieve_tmp --outputdir dx-converted
```

#### 7) Convert (dx format > metadata ):
```
sf project convert source -d output
```


#### 8) push/pull:
```
sf project retrieve start
```
```
sf project deploy start
```


#### 9) Generate password:
Generate:
```
sf org generate password
```
Display credentials info:
```
sf org display user
```

#### 10) Update CI variable
```
sf org login web -r https://test.salesforce.com -a sandBoxAlias
```
```
sf org display --verbose -o sandBoxAlias
```


#### 11) Mark Scratch Org for deletion:
```
sf org delete scratch -o scratchOrgAlias
```


#### 12) Deploy zip file:
Create connections in
To Sandbox:
```
sf org login web -d -r https://test.salesforce.com -a destOrgAliasSandbox
```
To Prod:
```
sf org login web -d -a destOrgAliasProd
```
Test deploy:
```
sf project deploy start --testlevel RunLocalTests --wait 60 --checkonly --zipfile zipName -o destOrgAlias
```
Real deploy:
```
sf project deploy start --testlevel RunLocalTests --wait 60 --zipfile zipName -o destOrgAlias
```


#### 13) Export data as plan:
```
sf data export tree -p -q "SELECT Id, Title__c, (SELECT Id, Country__c FROM Product_Countries__r) FROM Content_Product__c" -d ./your_data_folder 
```


#### 14) Import data as plan:
```
sf data import tree -p ./your_data_folder/import-plan.json
```


#### 15) Create connection for INT scratch org. _Please remove this point after transition to sandbox_
````
sf org login sfdx-url -f int-org.url
````
