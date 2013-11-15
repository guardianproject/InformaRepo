#Unveillance Backend 1.0

Setup:

You should already have Java installed (OpenJRE 7 is what I like) and JAVA_HOME variable should be set in your environment settings.

After cloning, run

    git submodule update --init --recursive

Install dependencies (not included in packaging):

    sudo apt-get install gcc build-essential yasm pkg-config libx264-dev python-dev python-setuptools lsof
    easy_install --upgrade google-api-python-client
    sudo pip install oauth2client
	sudo pip install urllib3

Install tornado, requests, filemagic, and fabric

    cd packages/[package]
    sudo python setup.py install

Install python-gnupg

	cd packages/python-gnupg
	sudo make install

Install FFmpeg

    cd packages/FFmpeg
    ./configure
    make
    sudo make install
  
Install FFmpeg2theora (not included in packaging):

    sudo apt-get install ffmpeg2theora

    
Config:

The configuration file must be completed.  It is located in:

    /conf/conf.py.example

Please copy the example to:

	/conf/conf.py

It's pretty well documented, but there is no setup wizard yet.
Subsequent versions of this package will make that easier.

Authentication:

- All private keys for accessing repositories (i.e. Globaleaks or GoogleDrive) MUST go in /conf.
- A gpg password file is required to use your secret key.  You may place this wherever you want.
- Your public key (which is shared to any user) can be placed wherever you want.

For all these files:

	chmod 0400 [file]

to protect them.

Forms:

We support OpenJDK/JavaRosa forms.  For more information on how to generate them, please visit http://www.kobotoolbox.org/
Subsequent versions of this package will include a form generator, but for now, you're on your own.  All forms MUST be placed in /forms

#USAGE

To install (no need to run after install-- it already does):
		
		cd /scripts/py/
		ln -s ../../conf/conf.py .
        sudo python unveillance.py install

To run:

        cd /scripts/py
        sudo python unveillance.py run

To stop:

        cd /scripts/py
        sudo python unveillance.py stop

