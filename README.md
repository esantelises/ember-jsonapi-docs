# Ember JSON API Docs [![Build Status](https://travis-ci.org/ember-learn/ember-jsonapi-docs.svg?branch=master)](https://travis-ci.org/ember-learn/ember-jsonapi-docs)

This app is for turning ember API doc build output into [json api](http://jsonapi.org/) compliant data for use in various applications seeking to use the Ember API.

The script pulls yuidoc build output from all Ember versions from Amazon S3, converts it to json api format and creates an archive.

## Running the app

1. Fork/Clone [ember-jsonapi-docs](https://github.com/ember-learn/ember-jsonapi-docs)
1. Run `yarn` or `npm install` (Needs node 6+)
1. Set up AWS access
    ```shell
    export AWS_ACCESS_KEY=xxxxxx
    export AWS_SECRET_KEY=xxxxx
    ```
    The app accesses builds.emberjs.com (an Amazon S3 bucket) in read-only mode, which is public. This requires any valid AWS credentials.

    You can get your credentials by logging into your [AWS console](https://console.aws.amazon.com) and navigating to "_My Security Credentials_" under your profile name. You can generate a new pair under the "_Access Keys (Access Key ID and Secret Access Key)_" section.
1. To test your changes in the app run,
   ```node index.js```
   Once complete, if no errors you should see a docs.tar file inside the `tmp` folder. The app tries to process all 
   ember & ember-data versions since 1.0 which takes high memory & time to complete. If you intend it, then run `node --max_old_space_size=8192 index.js`.
   You are setting your node max heap space to 8GB, so make sure you have that much space available on your machine.


## To Generate docs for a specific project and/or version for development 
You can do this by passing `--project ember/ember-data --version 2.11.1` as an argument to the index script. e.g., `yarn start -- --project ember --version 2.11.0`
