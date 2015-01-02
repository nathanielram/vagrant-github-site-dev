vagrant-github-site-dev
=======================

This was built to make it simple to develop with Jekyll for Github Pages.  

I built this to make it easy to work with Jekyll (a ruby gem) on Windows, which is done through the ease of use of Vagrant.

# How to use:

1. ```vagrant up```
2. ```vagrant ssh```
3. ```cd /vagrant```
4. ```bundle install```
5. ```bundle exec jekyll serve --watch --force_polling```
6. Visit 127.0.0.1:4000 in a browser
7. Ctrl+C and ```vagrant halt``` when done.

That should do it.
