# PINGURL

Friendly command line utility to ping a url, log its http status and notify you when it's not 200.

## Features

* Configure a conf file with your preferred settings
* [option] Set the interval at which the script should execute
* [option] Log the resulting http status in the file `ping_logs.txt` | format = [status][url][date]
* [option] Notify you at your email address when the status code is not 200

## Usage

1. Edit the `conf` file with your settings. See [Configuration](#conf).

2. Run the script

    ./ping_url
    
Example of console output

     ping_url done; status code = 200; url = https://github.com/; logs = ok; repeat in 1d...
    
Example of logs

      200 https://github.com/ Wed Apr 24 17:37:59 CEST 2013
      
## <a id="conf">Configuration</a>
