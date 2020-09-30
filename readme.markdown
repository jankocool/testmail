node-mail-relay

    use gmail with your custom domain for free

    SMTP server on port 587 for outgoing emails (set up your mail client to use this as a custom SMTP server)
    SMTP server on port 25 for incoming emails (forwards emails to you based on MAIL_MAP)

warning

This stuff is experimental. Use with caution.
install

$ npm i -g mail-relay

usage

$ mail-relay

In order to bind to port 25 and 587, you need to be root or you have to add CAP_NET_BIND_SERVICE to mail-relay. If you are concerned, run it as root, and drop privileges after start with SETUID.

A full configuration example:

$ AUTH_USER=foo \
  AUTH_PASS=bar \
  MAIL_MAP='{"john@doe.com":"johndoe@gmail.com"}' \
  SETUID=99 \
  mail-relay

configuration

With env vars.
AUTH_USER

User for the outgoing emails.
AUTH_PASS

Password for the outgoing emails.
MAIL_MAP

Address mapping

{
  "john@doe.com": "johndoe@gmail.com"
}

SETUID

Set uid after ports are bound (ie. you no longer run as root). You probably want to set it to $(id -u nobody) (which is 65534 or 99 or something else, depending on your system).
