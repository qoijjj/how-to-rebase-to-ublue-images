# How to rebase to ublue images

If you're a user who wants to use one of the `-main` or `-nvidia` images from ublue directly, you can do so easily with the following steps.

## Step 0: Choose which image you want

If you're not on nvidia, you can check the available images [here](https://github.com/orgs/ublue-os/packages?repo_name=main)

If you are on nvidia, you can check the the available images [here](https://github.com/orgs/ublue-os/packages?repo_name=nvidia)

## Step 1: Choose and install an official Fedora Atomic ISO

Those ISOs are available here: https://fedoraproject.org/atomic-desktops/

Choose the ISO that corresponds to the environment you'd like to use.

## Step 2: Rebase to the unsigned variant of the image you chose

For example, if you chose `kinoite-nvidia` in step 0, run the following commands:

```
rpm-ostree rebase ostree-unverified-registry:ghcr.io/ublue-os/kinoite-nvidia:latest
```

```
systemctl reboot
```

## Step 3: Rebase to the signed variant of the image you chose

For example, if you chose `kinoite-nvidia` in step 0, run the following commands:

```
rpm-ostree rebase ostree-image-signed:docker://ghcr.io/ublue-os/kinoite-nvidia:latest
```

```
systemctl reboot
```

## Step 4: Nvidia-only

Run `ujust configure-nvidia` to setup the kargs, then `systemctl reboot`

### Optimus laptops only

For optimus laptops, run `ujust configure-nvidia-optimus` to configure optimus laptops.
