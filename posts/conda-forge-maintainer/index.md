---
title: "Becoming a Conda-Forge maintainer"
author: "Robyn Marowitz"
date: "2023-09-26"
categories: [anaconda, github, open-science]
image: "featured_condaforge.png"
--- 

### What is Conda-Forge?
[Conda-Forge](https://github.com/conda-forge) is a community led collection of recipes, build infrastructure and distributions for the conda package manager.

There is an [NSIDC channel](https://anaconda.org/NSIDC) on conda-forge.  Most of these packages are now maintained on anaconda.org through the standard conda-forge. It s prefferred to use the [`conda-forge`channel](https://github.com/conda-forge) due to the checks and balances for maintaining that are kept up there.  

### Becoming a maintainer

I was working on a project and wanted to use `flask-dance`. The `flask-dance` docs were showing `v7.0.0` whereas [anaconda.org/conda-forge/flask-dance](https://anaconda.org/conda-forge/flask-dance/) showed `v2.2.0` and had not been updated in over 4 years. 

I did not want to be forced to install `flask-dance` using `pip` so I went over to the conda-forge [flask-dance repository](https://github.com/conda-forge/flask-dance-feedstock) on github. I saw that there was not an active maintainer and someone tried to [become one](https://github.com/conda-forge/flask-dance-feedstock/issues/7) back in 2021 to update the repository and had received no response. 

I used the [mainter docs](https://conda-forge.org/docs/maintainer/infrastructure.html#conda-forge-admin-please-add-user-username) to be added as a maintainer. I opened this [issue](https://github.com/conda-forge/flask-dance-feedstock/issues/10) which led to this [pull request](https://github.com/conda-forge/flask-dance-feedstock/pull/11) where I was added as a maintainer. Since it had been so long since there was an activate maintainer, I had to contact conda-forge/core and admin: ```@conda-forge/core please add me, the previous maintainer has not been active in years. @conda-forge-admin, please ping conda-forge/core```

### Updating a package
Once I got maintainer status I started the process of updating the `flask-dance-feedstock` so that I could start using it with conda. 

First I opened an [issue](https://github.com/conda-forge/flask-dance-feedstock/issues/12) asking to rerender. Which let to this [pull request](https://github.com/conda-forge/flask-dance-feedstock/pull/13). I actually made a small mistake here by not bumping the build number since this was simply a rerender and NOT a new build. This is outlined [here](https://conda-forge.org/docs/maintainer/updating_pkgs.html#updating-recipes) in the docs. I followed [these](https://conda-forge.org/docs/maintainer/updating_pkgs.html#archiving-feedstocks) instructions to fix my mistake with this [pull request](https://github.com/conda-forge/admin-requests/pull/817). You can now see the package marked as `broken` on [anaconda](https://anaconda.org/conda-forge/flask-dance/files). 

Once the rerendering was complete I started on the process of updating the recipe for `v7.0.0`. I followed the instructions on the [maintainer docs](https://anaconda.org/conda-forge/flask-dance/files) and forked the [repository](https://github.com/rmarow/flask-dance-feedstock). This was quite simple and can be seen in [this pull request](https://github.com/conda-forge/flask-dance-feedstock/pull/15). The automated checklists make the process very easy to follow. You will see that there is also rerendering as part of this process. Once I merged the pull request I soon saw the new package for `v7.0.0` on [anaconda](https://anaconda.org/conda-forge/flask-dance). 
