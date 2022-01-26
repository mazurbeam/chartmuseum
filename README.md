
### Environment
To run locally, create a `.env` and fill out values
```bash
AZURE_STORAGE_ACCOUNT=<accountname>
AZURE_STORAGE_ACCESS_KEY=<access_key>
CHARTMUSEUM_USERNAME=<username>
CHARTMUSEUM_PASSWORD=<password>
BASE_URL=<server_url>
```

Then run 

`
docker-compose up -d
`

### Creating and Uploading packages
See [docs](https://chartmuseum.com/docs/#uploading-a-chart-package) for more info

See Shared vault in 1Password for username:password

```bash
# create a helm template
helm create NAME

cd ./NAME
helm package .

# now you should have a .tgz file in the directory

curl -u <username>:<password> --data-binary "@NAME-0.1.0.tgz" https://chartmuseum.stackendsolutions.com/
```