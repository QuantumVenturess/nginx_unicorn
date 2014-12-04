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
$ boot2docker start # Start boot2docker so Docker runs on Mac
$ boot2docker ip    # Get the IP address of Docker containers
$ fig up            # Start development environment
```
Go to [ip_address]:3000 (ip address from `$ boot2docker ip`).

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
