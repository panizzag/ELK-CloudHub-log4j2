# logstash example config

```javascript
input {
	tcp {
		port => 5000
	}
}

## Add your filters / logstash plugins configuration here
filter {
	json {
			# Parses the incoming JSON message into fields.
			source => "message"
		}
}

output {
	elasticsearch {
		hosts => "elasticsearch:9200"
		user => "elastic"
		password => "changeme"
		codec => "json"
		index => "mule"
	}
}
```