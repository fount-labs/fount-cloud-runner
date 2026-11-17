# fount-cloud-runner

The Tinfoil config for a Fount Cloud runner enclave. Each release here is measured and
attested by Tinfoil; Fount's coordinator sends a job only to an enclave whose attestation
names a release of this repository.

The enclave runs two images, both built from
[fount-broker](https://github.com/fount-labs/fount-broker) by its release workflow and pinned
by digest in `tinfoil-config.yml`:

- **broker**: `fount-broker runner`. It takes each job over an attested link from the
  coordinator, holds the job's credentials and relays the rest to the supervisor.
- **supervisor**: `fount-supervisor serve`. It runs each job in gVisor, in the harness image
  pinned by the same config.

To release: pin the digests, then run **Tinfoil Release** with a new version.
