### Prerequisite
A [Backend API](https://github.com/udacity/cd0295-reactnd-contacts-server) should be up and running. Note the serving URL. 


### Deploy the Frontend App
1. Have your Frontend UI code point to the Backend API URL. 
```bash
cd reactnd-contacts-complete
```
Open the **src/utils/ContactsAPI.js** file, and update the `const api` URL. See an exmaple below:
```js
// Before
const api = process.env.REACT_APP_CONTACTS_API_URL || 'http://localhost:4000'
// After
const api = process.env.REACT_APP_CONTACTS_API_URL || 'http://reactnd-contacts-server-dev.us-east-1.elasticbeanstalk.com'
```
Use http (not https) and do not add any trailing slash (`/`) at the end of URL. 


2. Generate the artifacts to deploy:
```bash
rm -rf node_modules
rm -f package-lock.json
npm install
# Generate the new artifacts
npm run build
```
The build script will generate a `/build/` directory in the current directory. 


3. **Optional** - Deploy the UI code to S3 using the AWS CLI.
```bash
# List the buckets
aws s3 ls
# Assuming the bucket name is: myawsbucket-751397240855
```
Synchronize the content of the build folder into the S3 bucket.
```bash
# Change the bucket name as applicable to you
aws s3 cp --recursive --acl public-read ./build s3://myawsbucket-751397240855/
```
Navigate to the URL of your S3 bucket to ensure the deployments worked and that the website is healthy.


