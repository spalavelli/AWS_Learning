# access read olny permission s3 bucket and objects to particular user


## create s3 bucket

  * create Bucket name, cregion, in Object Ownership `ACL enabled`, 
  
  * uncheck ALL Block Public Access settings for this bucket (to acceass publicall) and create bucket.
 
  * click bucket which you have created go to permissions tab in that tab make sure this bucket publically accessbule or not.
  
  * Access control list (ACL) click `EDIT` and give raed permission Everyone (public access) (ckheck box) and re confirm it.
  
  * copy the ARN of the bucket 

## create user
  
  * create user and give custome polcie only read access to the user which bucket you want to read with `ANR URL` of the bukcet

## create custme policies
  
  * click create policie with json formate i.e like
  
  * attache to the user which you have created
  
  
{
        "Version": "2012-10-17",
        "Statement": [
                {
                        "Sid": "VisualEditor0",
                        "Effect": "Allow",
                        "Action": [
                                "s3:ListAllMyBuckets",
                                "s3:GetBucketLocation"
                        ],
                        "Resource": "*"
                },
                {
                        "Sid": "VisualEditor1",
                        "Effect": "Allow",
                        "Action": "s3:GetObject",
                        "Resource": "arn:aws:s3:::<bucket_name>/<object_name>/*"
                }
        ]
}
 
 
