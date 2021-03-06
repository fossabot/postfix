# postfix
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Ffametec%2Fpostfix.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Ffametec%2Fpostfix?ref=badge_shield)


Postfix SMTP Relay

## run

    docker run --rm -d --name postfix \
    -e RELAY_USER=postmaster@domain \
    -e RELAY_PASS=xxxxxxxxx \
    -e RELAY_HOST=smtp.mailgun.org \
    fametec/postfix:latest

## docker-compose

    version: '3.2'
    #
    ### Services
    #
    services:
    #
    # MAILGUN
    #
      relay:
        image: fametec/postfix:latest
        restart: unless-stopped
        volume: 
         - postfix-volume:/var/spool/postfix
        ports:
         - "30025:25"
        environment:
         RELAY_USER: postmaster@XXXXXXXXXXXXXXXX
         RELAY_PASS: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
         RELAY_HOST: smtp.mailgun.org
         
    #
    ### Volumes
    #
    volumes:
      postfix-volume:
      
      

 # testing

    echo "Email Test" | mail -s "This is a simple test" contato@fametec.com.br
 
or

    sendmail -f sender@example.com recipient@example.com
    From: Sender Name <sender@example.com>
    Subject: Amazon SES Test                
    This message was sent using Amazon SES.                
    .




## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Ffametec%2Fpostfix.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Ffametec%2Fpostfix?ref=badge_large)