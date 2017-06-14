# PINGURL

Friendly command line utility to ping a url, log its http status and notify you when it's not 200.

## Pitch

Because sometimes you need to ping a url for a rational reason or not. 
<br/><br/>This script was designed to ping a url for a given interval that you set.
It is best used if you need to continuously ping a url in the background and not worry about it until the status code changes. For this reason, 
the settings are done in a `conf` file at once. If you need to punctually ping a url, you can do this in a one liner, see <a href="#notes">Notes</a>. 

Also you have got to read the story of this script, you will love it forever:
http://machinesaredigging.com/2013/04/28/therapy-by-software/

## Features

* Configure a conf file with your preferred settings
* Set the url to ping in a conf file
* [option] Set the interval at which the script should execute
* [option] Log the resulting http status in the file `ping_logs.txt` | format = [status][url][date]
* [option] Notify you at your email address when the status code is not 200

## Requirements

* The `mail` utility if you want to be notified by email. To get it : `sudo apt-get install mailutils`
* The machine on which you run the script should have a smtp server enabled on it
* This script has been tested for Ubuntu 11.1

## Installation

1. [download](https://github.com/eloone/pingurl/archive/master.zip) the repository

## Usage

1. Set the url you want to ping in the `conf` file. Then edit the `conf` with your other settings. See <a href="#configuration">Configuration</a>.

2. Run the script from the repository folder

        ./ping_url
    
Example of console output

     ping_url done; status code = 200; url = https://github.com/; logs = ok; repeat in 1d...
    
Example of logs in `ping_logs.txt`

      200 https://github.com/ Wed Apr 24 17:37:59 CEST 2013
      
## Configuration

Configuration setting is done in the `conf` file.

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

If you don't want an option, delete the corresponding line or set its value to nothing. ex : `[optional] interval ::`

## Notes

To ping a url only once this line from the script is enough : 

        curl -sIL --url http://www.github.com -w "%{http_code} %{url_effective}" -o /dev/null

Yet, since it's rather ugly, you can also use the script and remove all the options from the `conf` file.
