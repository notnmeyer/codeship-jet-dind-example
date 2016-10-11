# codeship-jet-dind-example

If you build a Docker image with docker-in-docker and use a push step with a tag, the _service_ image is pushed and not the image defined in the push step. If you omit the 'image_tag' in the push step, the correct image is pushed.

Building the image in the services.yml may work, but for our particular use case we need build-args.

```
$ jet steps
$ docker run notnmeyer/codeship-test cat /id
The correct container

$ jet steps --push
$ docker run notnmeyer/codeship-test:blah cat /id
cat: can't open '/id': No such file or directory
```
