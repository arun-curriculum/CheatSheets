#Rails Production Cheatsheet

##Precompiling Assets

#####production.rb

Add your asset types that will be precompiled

```
config.assets.precompile = ['*.js', '*.css', '*.css.erb', '*.png', '*.jpg', '*.woff', '*.ttf']
```

#####If you need to prevent Rails from creating only assets with digests:

[Non Stupid Digest Assets](https://github.com/alexspeller/non-stupid-digest-assets)

```
gem "non-stupid-digest-assets"
```

An example of why you may need to use this is if you're using third party libraries that reference other files.

#####Run your rake task to precompile assets:

```
RAILS_ENV=production rake assets:precompile
```

##Set Up Configuration

#####Open up config/environments/production.rb and change the following value to true:

```
config.serve_static_assets = true
```

##Run Your Server

#####Start your server in daemon mode on port 80:

```
rvmsudo rails s -p 80 -d
```

##Database Configuration

If you have trouble installing Postgres or MySQL you may have to download and install the dev tools:

#####Postgres

```
sudo apt-get install libpq-dev
```

#####MySQL

```
sudo apt-get install libmysqlclient-dev
```