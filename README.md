# Localstack

Example code to test against AWS services locally using Localstack.


## Blog posts

Blog posts about this topic:

* [Local Development with AWS on LocalStack](https://reflectoring.io/aws-localstack/)

# Usage Examples of LocalStack


### Reference Documentation 

Two examples of using LocalStack is provided here. Make sure you have Docker installed and docker engine is started. The examples use Java 11. Make changes to pom.xml if you are using a lower version of Java.

* JUnit Test classes : JUnit Jupiter tests start LocalStack in a Docker container when the test runs and stops the container when test ends.
* Spring Boot application: REST API for creating a customer profile in AWS DynamoDB and store profile picture in S3. 

# Step
sudo apt-get install  awscli
sdk install java 11.0.18-sem
docker-compose up

//aws s3 --endpoint-url http://localhost:4566 create-bucket io.pratik.mybucket

aws cloudformation create-stack \
  --endpoint-url http://localhost:4566 \
  --stack-name samplestack \
  --template-body file://sample.yaml \
  --profile localstack


aws configure --profile localstack

export AWS_ACCESS_KEY_ID=AIOSFODNN7EXAMPLE
export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCEXAMPLEKEY

java -Dspring.profiles.active=local -jar target/customerregistration-1.0.jar

//to test
curl -X POST  -H "Content-Type: application/json"   -d '{"firstName":"Peter","lastName":"Parker",   "email":"peter.parker@fox.com", "phone":"476576576",            "photo":"iVBORw0KGgo...AAAASUVORK5CYII="          }'         http://localhost:8085/customers/