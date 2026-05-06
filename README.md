# oci-spec-playground

A hands-on exploration of the OCI ecosystem from first principles.

This repository explores the OCI Image and Distribution specifications through direct interaction with registries, manifests, blobs, artifacts, and tooling. The goal is not just to use OCI tooling, but to understand how OCI actually works on the wire and how modern build, artifact, and CI/CD workflows are constructed on top of it.

The repository combines:

- raw `curl` / `httpie` exploration of the OCI Distribution API
- direct inspection of manifests, indexes, configs, layers, and descriptors
- OCI artifact workflows using ORAS
- registry capability probing
- practical CI/CD and artifact promotion patterns
- experiments and notes while reading the OCI specifications

## Goals

### Learn OCI from first principles

Instead of immediately using higher-level tools, this repository starts by interacting directly with OCI registries using raw HTTP requests.

Examples include:

- `GET /v2/`
- fetching auth tokens
- resolving tags to digests
- retrieving manifests
- retrieving blobs
- understanding descriptors
- inspecting indexes vs manifests
- exploring referrers

The goal is to fully understand:

```text id="m9ovw9"
tag → index → manifest → config + layers
```

and how registries actually store OCI content.

### Understand OCI artifacts

The repository explores how OCI registries can be used for much more than container images.

Examples include:

- JAR files
- frontend distribution bundles
- SBOMs
- signatures
- provenance
- metadata artifacts

The repository explores:

- `artifactType`
- `subject`
- referrers
- annotations
- image manifests vs artifacts
- promotion by digest

### Learn ORAS workflows

After understanding the registry API directly, the repository explores ORAS and the workflows it enables.

Examples include:

- pushing arbitrary artifacts
- pulling artifacts
- attaching metadata
- discovering referrers
- exporting OCI layouts
- artifact graph exploration


### Explore registry behavior and capabilities

Different OCI registries behave differently.

This repository contains reusable commands and experiments for probing and validating registry capabilities such as:

- OCI artifact support
- referrers API support
- media type handling
- manifest compatibility
- annotation preservation
- image layout compatibility
- authentication behavior
- digest resolution
- multi-architecture support

Examples of registries explored may include:

- Docker Hub
- GHCR
- zot
- Harbor
- ECR
- GCR / Artifact Registry

### Explore OCI-based CI/CD patterns

The repository explores practical OCI-native workflows such as:

- build once, deploy many
- promotion by digest
- OCI artifact bundles
- separating build artifacts from runtime images
- attaching SBOMs and provenance
- image signing
- copying images and referrers between registries

## Repository Philosophy

This repository intentionally favors:

- explicit commands
- direct inspection
- understanding the underlying protocol
- small reproducible experiments
- spec-driven exploration

Many examples are intentionally shown first using:

```text id="a9hgtx"
curl
httpie
```

before showing the equivalent higher-level workflows with:

```text id="5p7gjx"
oras
docker
```
