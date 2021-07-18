# sketchbench-k8s

Collection of Helm Charts for SketchBench

## Examples

### `sketchbench-data-ingestion-espbench`

> Data Sender: [`sketchbench-data-ingestion-espbench`](https://github.com/SketchBench/sketchbench-data-ingestion-espbench)

#### With Bullet & Zeppelin

    helm install -f ./values-espbench-bullet.yaml my-sketchbench ./charts/sketchbench/

#### With Zeppelin (no Bullet)

    helm install -f ./values-espbench.yaml my-sketchbench ./charts/sketchbench/

### `sketchbench-data-ingestion-tester`

> Data Generator: [`sketchbench-data-ingestion-tester`](https://github.com/SketchBench/sketchbench-data-ingestion-tester)

#### With Bullet & Zeppelin

    helm install -f ./values-tester-bullet.yaml my-sketchbench ./charts/sketchbench/

#### With Zeppelin (no Bullet)

    helm install -f ./values-tester.yaml my-sketchbench ./charts/sketchbench/

---

### Accessing Bullet locally

> The following commands assume a Helm Release called `my-sketchbench`.

Two services are required to use the Bullet UI locally:

    kubectl port-forward service/my-sketchbench-bullet-ui 8800:8800
    kubectl port-forward service/my-sketchbench-bullet-web-service 9999:9999

## Resources

### Forward Kubernetes Services to localhost

> The following commands assume a Helm Release called `my-sketchbench`.

#### Bullet UI

    kubectl port-forward service/my-sketchbench-bullet-ui 8800:8800

#### Bullet Web Service

    kubectl port-forward service/my-sketchbench-bullet-web-service 9999:9999

#### Bullet Spark Backend UI

    kubectl port-forward service/my-sketchbench-bullet-spark-backend-ui 4040:4040

#### Bullet PubSub Monitoring UI (Kafdrop)

    kubectl port-forward service/my-sketchbench-pubsub-monit 9000:9000

#### Spark Web UI

    kubectl port-forward service/my-sketchbench-spark-master-svc 8000:80

#### HDFS Web UI

    kubectl port-forward service/my-sketchbench-hdfs-namenodes 9870:9870

#### Ingestion Kafka Monitoring UI (Kafdrop)

    kubectl port-forward service/my-sketchbench-kafka-monit 9000:9000

#### Zeppelin

    kubectl port-forward service/my-sketchbench-zeppelin 8080:8080

### Run `chart-testing` locally

#### Unix

`ct lint`:

    docker run --rm --volume .:/src --workdir /src quay.io/helmpack/chart-testing:latest ct lint --config ct.yaml

Interactive:

    docker run --interactive --tty --rm --volume .:/src --workdir /src quay.io/helmpack/chart-testing:latest bash

#### Windows

`ct lint`:

    docker run --rm --volume ${PWD}:/src --workdir /src quay.io/helmpack/chart-testing:latest ct lint --config ct.yaml

Interactive:

    docker run --interactive --tty --rm --volume ${PWD}:/src --workdir /src quay.io/helmpack/chart-testing:latest bash
