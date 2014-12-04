### Setup
```
$ ./initial_setup.sh              # Makes directories and copies unicorn.rb
$ cd rails_app                    # CD into the generic rails_app directory
$ rails new .                     # Create a new Rails app inside directory
$ echo 'gem "unicorn"' >> Gemfile # Add unicorn to Gemfile
$ bundle exec rake db:migrate
```

### Development
```
$ vagrant up
$ vagrant ssh core-01 -- -A       # SSH into the core
$ systemctl status bstrap.service # Check the status of systemd unit
```
Go to http://172.17.8.101:2375 to see the app

### Stop development processes
```
$ docker rm -f $(docker ps -a)
```

### Production
```
$ docker build -t [tag_name] .
$ docker run -d -p 3000:80 [tag_name]
```

### Errors
If unicorn doesn't start, delete /rails_app/shared/pids/unicorn.pid
