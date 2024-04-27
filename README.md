Login to your AWS account console.
Navigate to S3
Create a new bucket
Navigate to IAM 
Create a user Ex:Krishna with console access
Go to user > In permissions tab > Add permission > create inline policy
Add the below JSON code
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetBucketLocation",
                "s3:ListAllMyBuckets"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:ListBucketVersions",
                "s3:PutBucketVersioning"
            ],
            "Resource": [
                "arn:aws:s3:::s3timebased"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::s3timebased/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:ListBucketVersions",
                "s3:PutBucketVersioning",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::s3timebased/*"
            ],
            "Condition": {
                "DateGreaterThan": {
                    "aws:CurrentTime": "2024-04-27T19:47:00Z"
                },
                "DateLessThan": {
                    "aws:CurrentTime": "2024-04-27T19:55:00Z"
                }
            }
        }
    ]
}
