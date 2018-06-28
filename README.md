# ci-hello

# demo

(geinspireerd op https://github.com/making/concourse-ci-demo)

fly -t leo login -c https://concourse.gcp.npo-data.nl

# set up pipeline
cd ci
fly -t leo sp -p demo -c pipeline.yml -l credentials.yml # setup pipeline
fly -t leo ps # pipeline show
fly -t leo up -p demo # unpause
fly -t leo js -p demo # jobs show

fly -t leo tj -j helloworld/hello-world-job -w # trigger job & watch
