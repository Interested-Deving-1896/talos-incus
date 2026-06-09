[update-readmes]   Mode: rewrite — migrating to template structure...
# talos-incus

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/talos-incus)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/talos-incus.git
cd talos-incus
```

## Usage


```bash
# Use simplestreams remote (recommended)
incus remote add talos-incus https://images.interested-deving-1896.dev --protocol simplestreams
incus image list windsor:
incus launch windsor:talos/v1.12.0/amd64 my-instance
```

If you are using the Incus Terraform provider, you can add remotes in the `provider` block:

```
# Configure Incus provider with remotes for image pulls
provider "incus" {
  remote {
    name     = "talos-incus"
    address  = "https://images.interested-deving-1896.dev"
    protocol = "simplestreams"
    public   = true
  }
}

resource "incus_instance" "talos_controller" {
  name        = "talos-controller"
  description = "Talos control plane node"
  type        = "virtual-machine"
  image       = "talos-incus:talos/v1.12.0/arm64"
  ...
}
```

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/talos-incus`](https://github.com/Interested-Deving-1896/talos-incus) and mirrored through:

```
Interested-Deving-1896/talos-incus  ──►  OpenOS-Project-OSP/talos-incus  ──►  OpenOS-Project-Ecosystem-OOC/talos-incus
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
[MPL-2.0](https://github.com/Interested-Deving-1896/talos-incus/blob/main/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
