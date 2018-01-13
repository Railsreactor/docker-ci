# Rails Reactor Ruby Image for CI builds

Docker images used by Gitlab CI at RR

Get latest images here [https://hub.docker.com/u/railsreactor/](https://hub.docker.com/u/railsreactor/)

## Dependencies

* TODO: update this list

## Building

Ruby example

```
cd ruby
docker build -t railsreactor/docker-ci-ruby:1.23 .
docker login --username=railsreactor
docker push railsreactor/docker-ci-ruby
```

## Contributing

`Dockerfiles` are stored under folders for each version.

For updating the images, just open a _pull request_ with
the new `Dockerfile` version. Once built it will be 
published on https://hub.docker.com/r/railsreactor/
