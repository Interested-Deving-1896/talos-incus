[update-readmes]   Mode: rewrite — migrating to template structure...
# talos-incus

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/talos-incus)

<!-- AI:start:what-it-does -->
This project provides Talos Linux releases packaged specifically for use with Incus, a container and virtual machine manager. It automates the process of building, deploying, and mirroring Talos Linux images to ensure compatibility and streamlined distribution for Incus users.
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
The project packages Talos Linux releases for use with Incus. It consists of a Cloudflare Worker (`cloudflare-worker.js`) that handles requests and interacts with storage backends. Configuration is managed via `wrangler.toml.template`, and helper scripts are located in the `scripts` directory. GitHub Actions workflows (`.github/workflows`) automate tasks such as building releases (`build-multiple.yml`), deploying the worker (`deploy-worker.yml`), and mirroring images (`mirror-osp-to-ooc.yaml`). The directory structure is as follows:

```plaintext
.
├── .github/
│   └── workflows/
│       ├── build-multiple.yml
│       ├── deploy-worker.yml
│       └── mirror-osp-to-ooc.yaml
├── .gitignore
├── LICENSE
├── README.md
├── cloudflare-worker.js
├── scripts/
├── wrangler.toml.template
```
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
- **build-multiple.yml**: Builds Talos Linux images for multiple architectures. Runs on push and pull request events. No secrets required.

- **deploy-worker.yml**: Deploys the Cloudflare Worker defined in `cloudflare-worker.js` using Wrangler. Requires the `CF_API_TOKEN` secret for authentication.

- **mirror-osp-to-ooc.yaml**: Mirrors Talos Linux releases from an external source to the repository. Runs on a schedule. Requires `GITHUB_TOKEN` for repository access.
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
- [@Interested-Deving-1896](https://github.com/Interested-Deving-1896): 36 commits  
- [@rmvangun](https://github.com/rmvangun): 13 commits  
- [@renovate[bot]](https://github.com/renovate[bot]): 10 commits  

*Note: This repository is a mirror. Please refer to the upstream source for additional contributions.*
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
