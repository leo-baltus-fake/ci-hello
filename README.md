# ci-hello

# demo

(geinspireerd op https://github.com/making/concourse-ci-demo)

```
fly -t leo login -c https://concourse.gcp.npo-data.nl

```
# set up pipeline
```
cd ci
fly -t leo sp -p demo -c pipeline.yml -l credentials.yml # setup pipeline
fly -t leo ps # pipeline show
fly -t leo up -p demo # unpause
fly -t leo js -p demo # jobs show

fly -t leo tj -j demo/hello-world-job -w # trigger job & watch

fly -t leo bs # build show

fly -t leo cr -r demo/my-git-repo # may give a 500 if the resource cannot be checked
```
## execute tasks
https://concourse-ci.org/running-tasks.html

```
fly -t leo -c task.yml \
  --input foo=bar --input baz=bar --inputs-from main/hello_world
# execute without debugging commits, inputs are either hardcoded or taken from a previous pipeline
  --output foobar=/tmp/baz # use outputs.name foobar; /tmp/baz is populated on your local system
```
