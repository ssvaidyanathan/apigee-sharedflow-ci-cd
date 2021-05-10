# apigee-sharedflow-ci-cd

An CI/CD example to deploy Sharedflow and test it using a proxy

## License

This code is Copyright (c) 2017-2020 Google LLC, and is released under the
Apache Source License v2.0. For information see the [LICENSE](LICENSE) file.

## Disclaimer

This example is not an official Google product, nor is it part of an official Google product.

## Pre-requisites

- Node.js (10.x or later)
- Maven (3.x or later)
- Java (8 or later)

## Execution

This example deploys the Sharedflow to Apigee. To test the sharedflow, the test contains a simple proxy that calls this sharedflow and then executes some tests to verify if the sharedflow works as expected.

### Apigee Edge

To deploy the sharedflow 
	- Execute 
	```mvn clean install -Papigeeapi -Dorg=${org} -Denv=${env} -Dusername=${username} -Dpassword=${password}```

To test the sharedflow 
	- Execute 
	```mvn install -Papigeeapi -Dorg=${org} -Denv=${env} -Dusername=${username} -Dpassword=${password} -f test/integration/pom.xml```

To delete the Test API Products, Developer and App
	- Execute 
	```mvn apigee-config:apps apigee-config:apiproducts apigee-config:developers -Papigeeapi -Dorg=${org} -Denv=${env} -Dusername=${username} -Dpassword=${password} -Dapigee.config.options=delete -f test/integration/pom.xml```


### Apigee X / hybrid

To deploy the sharedflow 
	- Execute `mvn clean install -Pgoogleapi -Dorg=${org} -Denv=${env} -Dfile=${file} -Dapi.northbound.domain=${api.northbound.domain}`

To test the sharedflow 
	- Execute `mvn install -Pgoogleapi -Dorg=${org} -Denv=${env} -Dfile=${file} -Dapi.northbound.domain=${api.northbound.domain} -f test/integration/pom.xml`

