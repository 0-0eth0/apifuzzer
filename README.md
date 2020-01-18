# Fuzzapi

Fuzzapi is rails application which uses API_Fuzzer and provide UI solution for gem.

### New Scan
<img width="1679" alt="scan body" src="https://cloud.githubusercontent.com/assets/4562611/19390428/12224610-91f6-11e6-9ece-6e3cd7dd35ea.png">

### Scan Result
<img width="1679" alt="scan" src="https://cloud.githubusercontent.com/assets/4562611/19390442/1ef2f3d0-91f6-11e6-91eb-640b17d64a0b.png">

### Scan Histoy
<img width="1679" alt="scan2" src="https://cloud.githubusercontent.com/assets/4562611/19390533/79f83b96-91f6-11e6-9476-c3093b809674.png">

# Setup

1. Install ruby in your machine either using `rvm` or `rbenv`
Steps to install RVM:
  1) Open Your Terminal
  2) Enter following commands:
     `gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3`
     
     `\curl -sSL https://get.rvm.io | bash -s stable --ruby`
     
  3) If both commands works fine , enjoy your ruby coding withRVM else if it shows some error like:
    "Error running 'requirements_debian_libs_install gawk libyaml-dev libsqlite3-dev autoconf libgdbm-dev libncurses5-dev automake libtool', showing last 15 lines of /home//.rvm/log/1433925827_ruby-2.2.1/package_install_gawk_libyaml-dev_libsqlite3-dev_autoconf_libgdbm-dev_libncurses5-dev_automake_libtool.log"
    
  4) Then type this commands:
    `sudo apt-get install build-essential openssl libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion pkg-config`

 5) Now enter,
`\curl -sSL https://get.rvm.io | bash -s stable --ruby`

 6) If everthing works fine then enter this:
 `source /usr/local/rvm/scripts/rvm`
 
 7) Type "rvm" to make sure everthing is going perfectly
 
 8) now we need to install ruby-2.3.0, as this tool is compatible to only 2.3.0. so follow this commands,
 `rvm pkg install openssl #now while installing you will see final directory of install open ssl like this "Installing openssl to /usr/local/rvm/usr" note this directory", you will need this`
 
 `rvm remove 2.3.0 #if you installed`
 
`rvm install 2.3.0 --with-openssl-dir=/usr/local/rvm/usr #After "dir=" is your openssl installation directory`

 `rvm use 2.3.0  #Evrerytime you need to use while you shift to new tab of terminal or you open new window of terminal`
 
 9) `cd /path/Fuzzapi/bin`, move to Fuzzapi directory

10) `bundle update` & then to cross-check `bundle install` to install the gem dependencies of the application. (if you are getting some error related to any package search for its dependent packages and install them first. For example if error is related to pg `sudo apt-get install libpq-dev` then `gem install pg -v '0.18.4'`. Mostly people get errors related to nokogiri so here are the commands to resolve `sudo apt-get install build-essential patch` , `sudo apt-get install ruby-dev zlib1g-dev liblzma-dev` , `gem install nokogiri -v '1.6.8.1'`

11) `rake db:migrate` to creates tables, migrations etc.

12) Close everything and go to Fuzzapi/bin folder. "Dont Forget to type `rvm use 2.3.0`"

13) open three tabs of terminal "Dont Forget to type `rvm use 2.3.0`" on all three tables first

14) `redis-server` in first tab, Note: If redis-server is missing then install by simply typing `apt-get install -y redis-server`

15) In second tab `bundle exec sidekiq -r urFuzzAPIPath` 

16) In third tab `rails s` then visit `localhost:3000` and scan your sites

Fuzzapi comes with `Docker` to simplify installation processing. Following commands will setup application using `Docker`.

1) Clone the repository into your local machine

2) `cd /path/Fuzzapi`, move to Fuzzapi directory

3) Install Docker in your local machine

4) Run `docker-compose build` to build the image locally.

5) Run `docker-compose up` to run the server.

6) Open `http://localhost:3000` in browser which should point to the application url

Fuzzapi uses [API_Fuzzer](https://github.com/lalithr95/API_Fuzzer) gem.
