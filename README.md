### Serverless Lambda S3 Demonstration

This project demonstrates how the [Serverless Framework](https://serverless.com/) can be used to deploy a NodeJS Lambda function that responds to events in an S3 bucket.

In our demonstration, the Lambda function responds to image files uploaded to an S3 bucket, resize them, and writes the data to a corresponding image file in an output bucket.

### Getting Started

You will need to have the Serverless Framework installed globally with `npm install -g serverless`. In addition, you will need to [configure](https://serverless.com/framework/docs/providers/aws/guide/credentials/) Serverless Framework with your AWS credententials.

Next, go ahead and clone the project and install package dependencies.

- `git clone https://github.com/johncmunson/serverless-lambda-s3`
- `cd serverless-lambda-s3`
- `yarn` or `npm install`

Because the `serverless.yml` file is configured to provision any AWS resources that the Lambda function is dependent on, and because S3 bucket names must be globally unique, you will need to change `SOURCE-BUCKET-NAME-CHANGE-ME` and `RESIZE-BUCKET-NAME-CHANGE-ME` in `serverless.yml` to something that is meaningful but still unique.

At this point, the only thing left to do is deploy our function!

`serverless deploy -v`

### Testing it out

If everything went according to plan, you should be able to login to the AWS S3 console and upload any image file to the input bucket.

The deployed Lambda function will be triggered and should generate a resized image file that gets saved in the output bucket. Whether the function succeeded or failed, there should be some sort of output in AWS Cloudwatch.

### Cleaning Up

If you were just playing around with this project as a learning exercise, you may want to perform a bit of cleanup when you're all finished.

- Uninstall Serverless Framework: `npm uninstall -g serverless`
- Delete the local repository: `rm -rf serverless-lambda-s3`
- Cleanup AWS resources by deleting the Cloudformation stack
