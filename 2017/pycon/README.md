Effectively running python applications in Kubernetes/OpenShift
---------------------------------------------------------------

You can easily deploy the workshop materials using one of the following commands.

    docker run -ti \
        -v `pwd`:/content \
        -p 8080:8080 \
        -e CONTENT_URL_PREFIX="file:///content" \
        docker.io/osevg/workshopper

This will run a local docker image containing the [workshopper instace](https://github.com/osevg/workshopper).
You should be able to access it at [http://localhost:8080/](http://localhost:8080).
Don't forget to add `:Z` to volume when SELinux is enabled.

Alternatively, you can deploy it in OpenShift using:

    oc new-app \
        wildfly~https://github.com/osevg/workshopper.git \
        -e WORKSHOPS_URLS=https://raw.githubusercontent.com/soltysh/talks/master/2017/pycon/_workshop.yml \
        -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/soltysh/talks/master/2017/pycon \
        --name pycon-tutorial

    oc expose svc/pycon-tutorial

