# aws-in-5-mins
Aws how to in 5 mins

# Setup Cloudwatch on EC2
## Download and Install the ClousWatchAgent on EC2
- Amazon Linux 2

`sudo yum install amazon-cloudwatch-agent`

- Ubuntu x86_64

`wget https://s3.amazonaws.com/amazoncloudwatch-agent/ubuntu/amd64/latest/amazon-cloudwatch-agent.deb`

`sudo dpkg -i -E ./amazon-cloudwatch-agent.deb`

## Create agent configuration file
```
{
  "agent": {
     "metrics_collection_interval": 60,
     "region": "ap-southeast-1",
     "logfile": "/opt/aws/amazon-cloudwatch-agent/logs/amazon-cloudwatch-agent.log",
     "debug": false,
     "run_as_user": "root"
  },
  "logs": {
    "logs_collected": {
      "files": {
        "collect_list": [
          {
            "file_path": "/opt/aws/amazon-cloudwatch-agent/logs/amazon-cloudwatch-agent.log",
            "log_group_name": "amazon-cloudwatch-agent.log",
            "log_stream_name": "amazon-cloudwatch-agent.log",
            "timezone": "UTC"
          },
          {
            "file_path": "/opt/aws/amazon-cloudwatch-agent/logs/test.log",
            "log_group_name": "test.log",
            "log_stream_name": "test.log",
            "timezone": "Local"
          }
        ]
      }
    },
    "log_stream_name": "my_log_stream_name",
    "force_flush_interval" : 15
  }
}
```

