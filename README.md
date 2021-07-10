# sketchbench-k8s
Collection of Helm Charts for SketchBench

## Resources

### Run `chart-testing` locally

#### Windows

`ct lint`:

```bash
docker run --rm --volume ${PWD}:/src --workdir /src quay.io/helmpack/chart-testing:latest ct lint --config ct.yaml
```

Interactive:

```bash
docker run --interactive --tty --rm --volume ${PWD}:/src --workdir /src quay.io/helmpack/chart-testing:latest bash
```
