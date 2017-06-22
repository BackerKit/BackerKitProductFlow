Encapsulated classes don't seem to be tested. Private behavior?
Example: https://github.com/BackerKit/BackerKit/blob/a7deb3156748ed6d6801876d4d14f7e9f12209b6/app/mailers/daily_mailer.rb

* We seem not to want to lean on these going forward. For the time being we agree:
   * not to create more encapsulated classes.
   * to test or extract (and test) the ones we touch.
   
