# duplicity-restore-external
lifesaver for restoring external duplicity backups


## AWS
customize AWS and DEST Settings

  verify there are duplicity backups with awscli:
  
    user@host:~$ aws s3 ls s3://my-bucket-name/folder

if you don't remember file paths etc, copy the export lines from s3restore into your shell
and run the magic list command e.g:
```
    export AWS_ACCESS_KEY_ID="AWSACCESSKEY"
    export AWS_SECRET_ACCESS_KEY="AWSSECRETACCESSKEY"
    export PASSPHRASE="DUPLICITYENCRYPTIONPASSPHRASE"
    duplicity list-current-files --timeout=2400 --tempdir /tmp/dupltemp --num-retries=500 -t 6M s3://my-bucket-name/folder
```

run restore command:
```
    user@host:~$ bash s3restore 0D subfoldertorestore/subfolder2 destination
                                ^time |^location in bucket|        ^location on local machine to restore
```

e.g. 
bash s3restore 0D var/lib/docker /tmp/awsrestore/


