# Bartender: a wsgi server.

I wanted to do a simple git hook for a static website or two where the content was pulled down and converted from markdown with a little mermaid to static html. I have been doing this manually for a while but it gets to be a pain and besides all the kids are doing ci-cd and I thought it might help me actually write more.

Once apon a time when apache was really the best way to serve http writing interactive sites in python was a matter of enableing mod_wsgi and throwing up 20 lines of python. 

Gone are those days. 

Three days of swimming through uwsgi, unit and 3 other overtly complicated half thought out python solutions all of which require a separate standalone service I settled on a flask and gunicorn. Its still a kludgy pile. Time to go queue TurboNegros "I hate the kids" and just make it work.

## The Stack
```mermaid
    graph LR
    B -- http://127.0.0.1:8000--> C[nginx] -- http(s)://bartender/whisky/style --> I([Internet])
    A[flask] -- wsgi --> B[gunicorn];
```

```mermaid
  graph LR
  A[bartender] --> B[whiskey/neat] --> C[AT] --> 200/ok
  C --> D[pullandbuild.sh] --> G[github]
  G-->E
  D --> E[mkdocs build]

```
Installing the service.
```
apt install python3-flask
apt install python3-gunicorn

apt install at
echo www-data |tee /etc/at.allow
www-data

```
## linkdump
- https://github.com/codingforentrepreneurs/Pi-Awesome/blob/main/how-tos/Create%20a%20Minimal%20Web%20Application%20with%20Nginx%2C%20Python%2C%20Flask%20%26%20Raspberry%20Pi.md
- https://www.stackovercloud.com/2020/05/27/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-20-04/
- https://www.digitalocean.com/community/tutorials/how-to-set-up-uwsgi-and-nginx-to-serve-python-apps-on-ubuntu-14-04
- https://stackoverflow.com/questions/10748108/nginx-uwsgi-unavailable-modifier-requested-0#11055729

```

```