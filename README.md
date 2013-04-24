# PINGURL

Friendly command line utility to ping a url, log its http status and notify you when it's not 200.

## Features

* Configure a conf file with your preferred settings
* [option] Set the interval at which the script should execute
* [option] Log the resulting http status in the file `ping_logs.txt` | format = [status][url][date]
* [option] Notify you at your email address when the status code is not 200

## Usage

1. Edit the `conf` file with your settings. See <b>Configuration</b>.

2. Run the script

        ./ping_url
    
Example of console output

     ping_url done; status code = 200; url = https://github.com/; logs = ok; repeat in 1d...
    
Example of logs in `ping_logs.txt`

      200 https://github.com/ Wed Apr 24 17:37:59 CEST 2013
      
## Configuration

Configuration settings is done in the `conf` file.

---
     [required] url :: http://www.github.com

The url is required. The script will function with only that line in the conf file.

    [optional] interval :: 1d
    
The interval at which the script should execute. The format is the same as the arguments for `sleep`. See `man sleep`.

    [optional] logs :: true
    
If you wish to keep logs. The logs will be saved in the same directory in `ping_logs.txt`. Possible values = `true`, `false`.

    [optional] email :: notify@example.com
    
Set the email address at which you want to be notified when the status code is not 200.

---

If you don't want an option, delete the corresponding line or set its value to nothing.
