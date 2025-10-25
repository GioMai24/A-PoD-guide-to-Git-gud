# <p align='center'> Condacon </p>
Computer people struggle to make things work together. We don't like work, so we let computer people suffer for our sins.

Conda is one of those compartimentalization solutions. Instead of breaking things apart by installing python, R, and packages versions that hate each other, conda is smart (most of the time), and looks for compatible versions to get. It also lets you create different environments so you can keep enemies apart, while having 'up to date' packages.

## <p align='center'> Installation </p>
Install miniconda. It's way lighter and faster. You might think using GUIs doesn't hurt anyone. I will find you, and hurt you.

To install conda simply **READ THE DOCUMENTATION**: [miniconda docs](https://www.anaconda.com/docs/getting-started/miniconda/install#macos-linux-installation). If nothing's changed you should just run a `wget` command to download a script to run.

## <p align='center'> Creating envs </p>
Conda will create a `base` environment containing python. Never modify it. Always create your own environment for each scope you need. It's easy and fun, all you need is `conda create -n [NAME] [PACKAGES]`, on top of **READING THE DOCUMENTATION**. You can also install new packages in an existing env by `conda install -n [ENV NAME] [PACKAGE]`.

To search for a package you can either go to [anaconda.org](https://anaconda.org), which will also tell you the channel to use, or use `conda search [PACKAGE]`. The latter shows each available version of the package, from the selected channels. Channels are just sources where conda can look for packages.

Mostly you will want to download packages from `conda-forge`. To add a channel you merely add the option `-c [CHANNEL]` to the `conda create` or `conda install` command. If you want a package version from a specific channel you can do so via `[CHANNEL]::[PACKAGE]`. If you're lazy, you can even add conda-forge as a default channel by listing it in your `.condarc`[^1] file in your home directory.
[^1]: `rc` files are configuration files. Knowing how they work will let you customize many programs, including your bash. It's worth to take a look.

E.G.: `conda create -n juppy -c conda-forge python=3.12 jupyter ipykernel [MORE]`.

## <p align='center'> Use your envs </p>
I think I'll just vomit useful commands, but you know **DOCUMENTATION** exists:
- `conda info -e`: list your envs.
- `conda activate [NAME]`: access your env.
- `conda deactivate`: exit your active env.
- `conda list -n [ENV NAME] [PACKAGE]`: list all the installed packages in the selected env containing [PACKAGE] in their names. If no [PACKAGE] is provided, all the installed packages are listed.
- `conda remove -n [ENV NAME] --all`: delete your environment. You can also use `conda remove` to remove specific packages from an env.
- `conda clean -a`: remove tarballs and unused packages. This might save you a lot of space, so do not skip this after removing an env.

## <p align='center'> Share your env </p>
Sometimes you have to work with other people. People are desguhsting. Nonetheless you might want to share the same environment to avoid blaming the code for your poor work. To do so just **READ THE DOCUMENTATION** that will tell you to `conda export -n [ENV NAME] > [NAME].yaml`. Beware the last line holding the path, or 'prefix', to the environment creation. People should change that before creating the env.

To create an env from a file you can use `conda create -f [FILENAME]`. Simple as that. Again: check the prefix definition.

---

## <p align='center'> Why is there no R? </p>
There is, you haven't **READ ENOUGH DOCUMENTATION**. Since I'm way too nice with you, I'll also help you with it. You'll need R in the second semester with ASPA.

I think all R libraries are named in a `r-[LIBRARY]` fashion[^2]. R itself is called `r-base`.
[^2]: I used only a few libraries, so TeCHniCaLLy I haven't checked every single one.

When you try to install or use them, it is possible they will complain about missing dependencies on your system. They possibly are not conda stuff, but actual libraries to install in your Linux system[^3]. Just install them, write their name down somewhere to `sudo apt-get purge` the sh!t out of them when you'll get rid of R.
[^3]: If you're using Windows or MacOS you're stupid, and I hate you.

E.G.: `conda create -n argh -c conda-forge r-base r-tidyverse jupyter irkernel`.
