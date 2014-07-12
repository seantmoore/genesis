genesis
=======

**TL;DR:** Script to download, install, and configure Django, Postgres, Nginx, and Gunicorn all in one go on a fresh Ubuntu install.

=======

## Intro

Most of my projects start with me spinning up the smallest droplet from Digital Ocean and then following their guide[0] for installing Django, Postgres, Nginx and Gunicorn. Well I decided to mash all those commands into a bash script to do all that for me. I've also updated the script in a few places where the guide is out of date.

I'm sure this script will work on a few OSes with some massaging, but all I can say is that I've tested it on Digital Ocean's smallest droplet using Ubuntu 14.04 and it seems to work.

I don't write bash scripts often, so I'm sure the script will horrify anyone who writes them on a regular basis, but, like I said, it seems to work for my purposes.

## Things to note

First thing to note is that this script, as is, should be used for DEVELOPMENT only. It sets up things using a lot of the defaults and probably with bad practices.

This script assumes a clean Ubuntu 14.04 install with a user other than root that has sudo access.

There are two variables at the top DJANGO_PROJECT_NAME and POSTGRES_DB_NAME. These should be edited to reflect what you want to call your project and your database.

The main database is set up with "postgres" as the main user so no DB permissions or users need to be set up. This also is not the way you should set up Postgres in a production environment.

Step 2 from the guide is skipped. This script assumes a clean slate and therefore no need for virtualenv.

## Zero to Django (step by step)

0) Have an account at DigitalOcean.com

1) Create a new droplet and use Ubuntu 14.04

2) Sign in and secure the root account (either a ridiculously long (but memorable) password or ssh key + turn off password access)

3) Create a new user and give that user sudo access.

4) Sign in with that user

4.1) Optional: update and upgrade (sudo apt-get update; sudo apt-get upgrade). The script does this but you might want to separate the output.

5) git clone (or just download+unzip) this project to your home directory

6) from your home directory: 

- **$** cd genesis/
- **$** chmod 777 genesis.bash
- **$** ./genesis.bash > /dev/null

Note: Relevant output from the script is piped to stderr for readability.

7) Relax (unless your droplet has exploded, then panic!)

## I told you so (disclaimers)

I don't work for Digital Ocean, I just appreciate that their smallest droplet is 1/3 the price of AWS (or similar).

I promise nothing. I'm a programmer, but I almost never write bash scripts. This script has worked a few times for me and I thought it might be useful for people who are constantly spinning up new Django projects.

If it works for you, great! If not, sorry about that. You can try and mess around with it. All the basic steps from the guide should be there.

=======

### Citation(s):

[0] https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-django-with-postgres-nginx-and-gunicorn