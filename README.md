# NVIDIA CUDA Toolkit SDK for Workshop

NVIDIA CUDA is a parallel computing platform and programming model for NVIDIA
GPUs. This SDK installs the CUDA Toolkit inside the workshop during setup-base
using the official NVIDIA CUDA APT repository, placing everything under
`/usr/local/cuda`.

---

## Reference workshop

A minimal workshop:

```yaml
# workshop.yaml
name: cuda-dev
base: ubuntu@24.04
sdks:
  - name: cuda-toolkit
    channel: 12.9/stable

actions:
  check-gpu: |
    nvidia-smi
  compile-sample: |
    cd /project
    nvcc -o sample sample.cu
    ./sample
```

This demonstrates GPU access and CUDA compilation inside a workshop.

### Available tracks

| Track | CUDA series | Platforms |
|-------|-------------|-----------|
| `12.9/stable` | CUDA 12.9.x | ubuntu@22.04, ubuntu@24.04 |
| `12.8/stable` | CUDA 12.8.x | ubuntu@22.04, ubuntu@24.04 |
| `12.6/stable` | CUDA 12.6.x | ubuntu@22.04, ubuntu@24.04 |
| `11.8/stable` | CUDA 11.8.x (frozen) | ubuntu@22.04 only |

---

## Using the SDK

### Prerequisites, project layout

The SDK installs the NVIDIA CUDA Toolkit from the official NVIDIA APT
repository and automatically configures `PATH` and library paths. An NVIDIA
GPU with a compatible driver must be available on the host.

No specific project layout is required. Place your `.cu` files in the project
directory.

### Run CUDA samples

To build a project or run CUDA examples in the workshop:

```bash
git clone https://github.com/NVIDIA/cuda-samples.git
workshop launch
workshop shell
```

Inside the workshop:

```bash
cd /project/cuda-samples/Samples/1_Utilities/deviceQuery
make
./deviceQuery
```

### Verify GPU access

Once the workshop is ready:

```bash
workshop shell
nvidia-smi
```

This shows detected NVIDIA GPUs, driver version, and CUDA version. To verify
the compiler:

```bash
nvcc --version
```

---

## Plugs (resources this SDK consumes)

### `gpu`

- Interface: `gpu`
- Purpose: Grants access to NVIDIA GPU hardware on the host.

## Slots (resources this SDK provides)

This SDK doesn't define any slots.

---

## Documentation and guidance

- [CUDA Toolkit documentation](https://docs.nvidia.com/cuda/)
- [CUDA samples](https://github.com/NVIDIA/cuda-samples)
- [Workshop documentation](https://ubuntu.com/workshop/docs/)

---

## Community and support

- NVIDIA developer community:
  [NVIDIA Developer Forums](https://forums.developer.nvidia.com/)
- Workshop forum:
  [Discourse](https://discourse.ubuntu.com/)
- Please review our
  [Code of Conduct](https://ubuntu.com/community/ethos/code-of-conduct) before
  participating.

---

## Contributions

All contributions, including code, documentation updates, and issue reports,
are welcome!

- See `CONTRIBUTING.md` for guidelines.
- Open issues or pull requests on the official repository.

---

## License and copyright

Copyright 2026 Canonical Ltd.

This program is free software: you can redistribute it and/or modify it under
the terms of the
[GNU Lesser General Public License version 2.1 (LGPLv2.1)](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html)
as published by the Free Software Foundation.

[NVIDIA CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit) is subject to
the [NVIDIA CUDA Toolkit EULA](https://docs.nvidia.com/cuda/eula/).
