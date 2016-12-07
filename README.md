# Rails Reactor Ruby Image for CI builds

Docker images used by Gitlab CI at RR

## Dependencies

* TODO: update this list

## Building

Ruby example

```
cd ruby
docker build -t railsreactor/docker-ci-ruby:latest -t railsreactor/docker-ci-ruby:1.0 .
docker login --username=railsreactor
docker push railsreactor/docker-ci-ruby
```

## Contributing

`Dockerfiles` are stored under folders for each version.

For updating the images, just open a _pull request_ with
the new `Dockerfile` version and, after accepted, Docker
Hub will build automatically after a few minutes.
