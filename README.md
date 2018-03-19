
JupyterHub private unverse
==========================

This private-universe contains only jupyterhub custom package.

Build
-----

0. Clone `git clone https://github.com/mesosphere/universe` on the sibling level. And cd to that folder.

> Note: you will need pip, Docker, jq and other tools to build it. See universe github for more details.

1. Build stub:
```
scripts/gen_universe.py --repository ../private-universe/packages/ --out-dir ../private-universe/repo
```
It will generate private repo files in `../private-universe/repo`

2. Upload to your S3 bucket with predefined Content-Type:
```
aws s3 cp --content-type "$(cat ../private-universe/repo/repo-up-to-1.11.content_type)" ../private-universe/repo/repo-up-to-1.11.json s3://ygribkov/jupyterhub-repo/ --acl public-read
```

3. Add to DC/OS or access it by: (https://s3.amazonaws.com/ygribkov/jupyterhub-repo/repo-up-to-1.11.json)

Add repo to DC/OS: `dcos package repo add --index=0 "Private Universe" https://host/and/path/to/repo-up-to-x.json`

Your packages ready to be installed.

Here is official doc for private-universe: `https://github.com/mesosphere/universe/blob/version-3.x/docs/gen_universe/gen_universe.markdown`