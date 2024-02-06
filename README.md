# LunAPI: A Python interface for Luna

This repository contains tutorial and reference notebooks for LunAPI
(pronounced _luna-py_), a Python-based interface for the
[Luna](http://zzz.bwh.harvard.edu/luna/) C/C++ toolset for the
analysis of sleep signal data.

## Getting started

While we develop the `lunapi` Python package, we are primarily
supporting a Docker-based installation.  This ensures that the same
functionality is available on all platforms (Windows, macOS and Linux)
and allows `lunapi` to be bundled with a set of associated models and
resources (e.g. tutorial data, staging models, etc) embedded within a
Jupyter Lab interactive notebook environment.

There are four easy steps:

 - Install [Docker Desktop](http://www.docker.com)

 - Pull the `lunapi` Docker image:
   ```
   docker pull remnrem/lunapi
   ```

 - Grab the notebooks in this repo:
   ```
   git clone https://github.com/remnrem/luna-api-notebooks.git
   ```

 - Fire up a container with Jupyter Lab bundled with Luna and other resources:
   ```
   docker run --rm -p 8888:8888 -v ${PWD}:/lunapi/ remnrem/lunapi
   ```

See the notes below for more details.

 
> [!NOTE]
> We will soon be distributing binary wheels for all major
> platforms and Python versions via PyPI.  In the mean time,
> experienced users are free to compile the project locally
> (i.e. pre-installing [Luna](http://github.com/remnrem/luna-base) and
> [LunaAPI](http://github.com/remnrem/luna-api) and invoking
> the scikit-build-core/CMake build system).
> Notes on this process will be
> added in the future: for now, this Docker version is the suggested
> way to get started.

### 1) Install Docker Desktop

First, download a free copy of [Docker Desktop](http://www.docker.com)
for your machine.  If using a Mac, be sure to select the correct chip
type (Apple vs Intel).

<p align="center" width="100%">
 <img src="img/docker1.png" width="70%" height="70%">
</p>

There is plenty of help on the Docker pages if you get stuck.

### 2) Pull the latest LunAPI image

After installing Docker, use the command line to _pull_ the latest version
of `lunapi`:

```
docker pull remnrem/lunapi
```

<p align="center" width="100%">
 <img src="img/pull.png" width="100%" height="100%">
</p>

> [!TIP]
> You can always use this command subsequently to check that the version you are using
> is up-to-date.


### 3) Get the tutorial and reference notebooks

Next, get the tutorial and reference notebooks from this repository. These are not required
but will be helpful to get you started.   For example, you can use `git clone` from the command line,
or simply download a Zip file from the links at the top of this page:

<p align="center" width="100%">
 <img src="img/download.png" width="50%" height="50%" align="center">
</p>

### 4) Start LunAPI 

Move to the folder where you downloaded the notebooks (`luna-api-notebooks/`)
and start _LunAPI_ by running this Docker command:  (this is the point you'd start from
having already downloaded the above, i.e. when starting a new session):

```
docker run --rm -p 8888:8888 -v ${PWD}:/lunapi/ remnrem/lunapi
```

<p align="center" width="100%">
 <img src="img/run.png" width="100%" height="100%" align="center">
</p>

> [!NOTE]
> See the Docker documentation for more details on using
> Docker.  The above command `run`'s the image `remnrem/lunapi`
> (i.e. as you just downloaded from the
> [DockerHub](http://hub.docker.com) repository).  The additional
> options 1) stop the container when you finish (`--rm`), 2) map port
> 8888 from the container to port 8888 on your machine, so that you
> can access Jupyter Lab via your local web browser, and 3) map the
> current folder on your local machine (`${PWD}`) to the folder
> `/lunapi/` in the container, so that you can read/write files to
> your machine from the container.  See Docker options for more
> functions, e.g. it is easy to map multiple folders (or specify a
> folder other than the working directory, e.g. `-v
> /home/john/data/:/lunapi/` using the form `local:container`), etc.
> One tip is that it is better not to map your whole home folder for
> performance reasons.

After running the above, you should see some text from Jupyter Lab's
start-up log in the window (most of which you can safely ignore,
including various warnings that may subsequently appear from JupyterLab 
in that terminal window).  We'll try to streamline this later, but for now:
to access Jupyter Lab, look for the line (it may appear twice) starting
`http://127.0.0.1` (which is your local machine), for example:

<p align="center" width="100%">
 <img src="img/start.png" width="100%" height="100%" align="center">
</p>

e.g. in this particular instance, this is the link to be copied:
```
http://127.0.0.1:8888/lab?token=df46b121be42d19f70d647af90b569b1240c668f41bf1b57
```
> [!TIP]
> Note that the token will be different each time, do not try to use the exact link above.

Copy-and-paste the whole line (with the token) into your web browser and you
should see an instance of Jupyter Lab is already running and ready to
start analysis! For example, here we first `import lunapi as lp` and then run
the POPS automated stager on an NSRR tutorial EDF:

<p align="center" width="100%">
 <img src="img/nb.png" width="100%" height="100%">
</p>

For more details, open the notebooks (`.ipynb` files) to follow the tutorial and reference material for `lunapi`.  

Keep the terminal window open (can be backgrounded) in order to keep the Jupyter Lab instance
running locally on your machine.

> [!CAUTION]
> Without altering configuration files, you can only have a single instance of Jupyter Lab and LunAPI container running
> at any one time.

## More information

The main Luna documentation pages can be found at
[http://zzz.bwh.harvard.edu/luna](http://zzz.bwh.harvard.edu/luna), which describes how to work with Luna,
its command scripting language and the range of analyses available.

Currently, all documentation related to the Python interface
(i.e. _LunAPI_, equivalently termed as the Python package `lunapi`)
are in the Jupyter notebooks in this repository.

