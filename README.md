# hubot-macpaw

Automate your business and have fun with your very own robot companion.

## Documentation

Please visit [hubot.github.com](https://hubot.github.com/docs/scripting/) for original hubot documentation.

###Run the test bot

It is a good idea to test your funny(or not) scripts before you roll out it to the team channels!
There is a test bot, and you can run with the following command:

```
docker build --tag=hubot-test . && docker rm -f $(docker ps -a -q) || true && docker run -it --env-file ./build/ENV -v /etc/localtime:/etc/localtime:ro -p 8080:8080 --name hubot-test hubot
```
If you don't see any issues, and your console looks like that:
```
[Tue Aug 08 2017 18:53:40 GMT+0000 (UTC)] INFO Logged in as hubot-test of macpaw
[Tue Aug 08 2017 18:53:40 GMT+0000 (UTC)] INFO Slack client now connected
[Tue Aug 08 2017 18:53:41 GMT+0000 (UTC)] INFO Using default redis on localhost:6379
```

join the #hubot-test-channel channel and ask hubot to show you some nice cat:

```
@hubot-test cat me
```
or test your new scripts


###Run the production bot

The production Hubot is running on the [Docker Cloud](https://cloud.docker.com)!
Also, in the docker cloud, you can find the environment variables! The public production endpoint for hubot is hubot.appflix.io:8080.
Сredentials for docker cloud console you can find in 1password Ops Vault. 
To deploy a new version of the bot it is enough to build and push the image to the docker registry, and it redeploys it automatically.

```
docker build --tag=hubot:prod .
docker tag hubot:prod macpaw/hubot:prod && docker push macpaw/hubot:prod
```
