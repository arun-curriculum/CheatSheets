#Deploying a Rails Site to AWS

##Setup
1. Create AWS account [here](http://aws.amazon.com/).
2. Go to EC2 dashboard.
3. Click "Launch Instance"
4. Select Ubuntu.
5. Click "Next"
6. Click "Review and Launch"
7. Click "Edit Security Groups"
8. If you don't already have a security group set up, create a new one.
9. Click "Add Rule" and add HTTP to the security group.
10. Click "Review and Launch" again.
11. Click "Launch".
12. Create a new PEM file key if you don't have one already. You can only download this once so keep it safe!

##Login to Your Server

When the server is up and running, you will be able to log into it. This is handled through the terminal using Secure Shell (SSH).

1. From the EC2 dashboard, select your instance.
2. You will see a "public DNS" option showing your instance's current URL. It will look something like this: ec2-54-148-134-239.us-west-2.compute.amazonaws.com.
3. CD into your directory containing your 
4. Open your terminal and type the following command:

`ssh -i YourPemFile.pem ubuntu@yourpublicdnsurl`

5. When it asks you if you want to continue type "yes" and hit enter.
6. If PEM file is refused you will have to update its permissions:

`chmod 400 YourPemFile.pem`

##Update Server and Install Git

Update the Ubuntu package manager:

`sudo apt-get update`

Install Git:

`sudo apt-get install git`

##Install RVM and Ruby

Install RVM:

`\curl -sSL https://get.rvm.io | bash -s stable`

If that fails and says something like this:

`GPG signature verification failed for '/home/ubuntu/.rvm/archives/rvm-1.26.3.tgz' - 'https://github.com/wayneeseguin/rvm/releases/download/1.26.3/1.26.3.tar.gz.asc'!
try downloading the signatures:`

You need to run the command they specify, then re-run the install RVM command. It looks something like this:

`gpg --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3`

It will prompt you to run a command like this to get RVM to work:

`source /home/ubuntu/.rvm/scripts/rvm`

Install Ruby:

`rvm install ruby`

Install Rails:

`gem install rails --no-ri --no-rdoc`

##Set up Your Project
1. Git clone your project.
2. Bundle install.
3. Rake db:migrate.
4. Start the server.
5. Good to go!