# Railsreactor Ruby Image for CI builds

Docker Ruby images used by Gitlab CI.

## Dependencies

The following dependencies are being installed on all images:

* Node.js v4.4.7 and npm
* PhantomJS v1.9.8
* Qt v5 and Xvbf (only on CRuby images)
* TODO: update this list

## Tags

We currently have images for the following Rubies.

### CRuby images

- `2.3`, `latest` [Dockerfile](https://github.com/Codeminer42/docker-ci-ruby/blob/master/2.3/Dockerfile)

## Contributing

`Dockerfiles` are stored under folders for each version.

For updating the images, just open a _pull request_ with
the new `Dockerfile` version and, after accepted, Docker
Hub will build automatically after a few minutes.
