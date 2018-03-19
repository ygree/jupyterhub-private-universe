
JupyterHub private unverse
==========================

This jupyterhub-private-universe contains only jupyterhub custom package.

Build
-----

0. Clone `git clone https://github.com/mesosphere/universe` on the sibling level. And cd to that folder.

> Note: you will need pip, Docker, jq and other tools to build it. See universe github for more details.

1. Build stub package: see `build` script

2. Upload logos: see `upload-logos` script

3. Publish stub to S3: see `publish` script

3. Add to DC/OS or access it by: (https://s3.amazonaws.com/ygribkov/jupyterhub-repo/repo-up-to-1.11.json)

Add repo to DC/OS: `dcos package repo add --index=0 "Private Universe" https://s3.amazonaws.com/ygribkov/jupyterhub-repo/repo-up-to-1.11.json`

Your packages ready to be installed.

Here is official doc for private-universe: `https://github.com/mesosphere/universe/blob/version-3.x/docs/gen_universe/gen_universe.markdown`