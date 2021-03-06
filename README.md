# infra_helpers
Repo for scripts/tools for DevOps things.

## aws/aws_route53_register_deregister_instance.py
Script used to add or remove instance public IP to Route 53. Uses weighted routing to divide IPs into buckets.

Usage:

`python3 aws_route53_register_deregister_instance.py --record_name DOMAIN_NAME --record_type RECORD_TYPE --record_ttl RECORD_TTL --hosted_zone_id HOSTED_ZONE_ID --action add`

For example:

`python3 aws_route53_register_deregister_instance.py --record_name record.example.com --record_type A --record_ttl 60 --hosted_zone_id HOSTED_ZONE_ID --action add`

For removing entries, use `--action remove`.

## aws/aws_elb_check_elb.py
Script to do health check on ELB instances and check HTTP 200 code. Needs AWS ELB DNS and health check path. It will get public IPs of all ELB instances and see if the health check endpoint is being correctly forwarded to the backend instances.

Usage:

`python3 aws_elb_check_elb.py --elb_name http://elb.region.elb.amazon.aws.com --path health_check_path`

## general/backoff_strategies.py
Some code demonstrating different backoff strategies for retrying after transient failures.

## general/post_to_slack.py
Sample script to post messages to Slack using incoming webhooks.

## influxdb/backup_influxdb_to_s3.sh
Automatically backup all InfluxDB databases to S3.

Usage:

`./backup_influxdb_to_s3.sh s3://example_bucket/folder/`

## mysql/backup_mysql_to_s3.sh
Script used to take GZIPed backup of database and upload it to S3.

Usage:

`./backup_mysql_to_s3.sh s3://example_bucket/folder/`

+ Add it to cron to automate DB backups.
+ Add lifecycle policies to target S3 bucket to control previous versions.

