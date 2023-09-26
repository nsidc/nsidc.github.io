---
title: "Becoming a Conda-Forge maintainer"
author: "Robyn Marowitz"
date: "2023-09-26"
description: "NSIDC is transitioning to managing conda build recipes using conda-forge. This post will describe how that experience is advancing our practices."
categories: [anaconda, github, open-science]
image: "featured_condaforge.png"
--- 

### What is Conda-Forge?
[Conda-Forge](https://github.com/conda-forge) is a community led collection of recipes, build infrastructure and distributions for the conda package manager.

There is an [NSIDC channel](https://anaconda.org/NSIDC) on Anaconda.org that we used to publish to. We are shifting to maintain conda distributions through the `conda-forge` community, starting with `earthaccess`. It is prefferred to use the [`conda-forge`channel](https://github.com/conda-forge) due to the checks and balances for maintaining that are standard through the automation and documentation provided for the community.

### Becoming a maintainer

I was working on a project and wanted to use `flask-dance`. The `flask-dance` docs were showing `v7.0.0` whereas [anaconda.org/conda-forge/flask-dance](https://anaconda.org/conda-forge/flask-dance/) showed `v2.2.0` and had not been updated in over 4 years. 

I prefer to install `flask-dance` as a `conda` package, so I went over to the `conda-forge` [flask-dance-feedstock repository](https://github.com/conda-forge/flask-dance-feedstock) on GitHub. I saw that there was not an active maintainer and someone tried to [become one](https://github.com/conda-forge/flask-dance-feedstock/issues/7) back in 2021 to update the repository and had received no response. 

Becoming a maintainer was easy! Following the [maintainer documentation](https://conda-forge.org/docs/maintainer/infrastructure.html#conda-forge-admin-please-add-user-username),  I opened an [issue](https://github.com/conda-forge/flask-dance-feedstock/issues/10) which led to the automatic ceation of a [PR](https://github.com/conda-forge/flask-dance-feedstock/pull/11) to add myself as a maintainer. Since it had been so long since there was an activate maintainer, I contacted conda-forge/core and admins and advised by the docs: ```@conda-forge/core please add me, the previous maintainer has not been active in years. @conda-forge-admin, please ping conda-forge/core```

### Updating a package
Once I received maintainer permissions I started the process of updating the `flask-dance-feedstock` to release the newest version.

First I needed to re-render the feedstock. conda-forge includes tens of thousands of projects, so it's important that improvements are shared across all projects. This process is handled by bots which re-generate project files in response to certain events. To trigger a re-render I opened an [issue with a specific title](https://github.com/conda-forge/flask-dance-feedstock/issues/12), which led to automatic creation of this [pull request](https://github.com/conda-forge/flask-dance-feedstock/pull/13). I made a small mistake here by not bumping the build number since this was simply a re-render and NOT a new version. This resulted in a duplicate package being published. The rules for updating the build number are outlined [in the docs](https://conda-forge.org/docs/maintainer/updating_pkgs.html#updating-recipes). I followed [these instructions](https://conda-forge.org/docs/maintainer/updating_pkgs.html#archiving-feedstocks) and fixed my mistake with this [pull request](https://github.com/conda-forge/admin-requests/pull/817). You can now see the incorrect package marked as `broken` on [anaconda](https://anaconda.org/conda-forge/flask-dance/files). 

Once the rerendering was complete I started on the process of updating the recipe for `v7.0.0`. I followed the instructions on the [maintainer docs](https://anaconda.org/conda-forge/flask-dance/files) and forked the [repository](https://github.com/rmarow/flask-dance-feedstock). This was quite simple and can be seen in [this pull request](https://github.com/conda-forge/flask-dance-feedstock/pull/15). The automated checklists make the process very easy to follow. You will see that there is also rerendering as part of this process. Once I merged the pull request I soon saw the new package for `v7.0.0` on [anaconda](https://anaconda.org/conda-forge/flask-dance). 

## Becoming a conda-forge maintainer makes releasing conda packages easy

I found it very easy to become a maintainer. The documentation is really straight forward and the community is supportive and responsive.   
