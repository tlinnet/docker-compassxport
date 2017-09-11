# CompassXport Docker Buildfile
- This repository <https://github.com/tlinnet/docker-compassxport> was forked from <https://github.com/phnmnl/docker-compassxport> September 2017.

The first step in a metabolomics data processing workflow with Open
Source tools is the conversion to an open raw data format like
[mzML]:<https://github.com/HUPO-PSI/mzML> .

For Bruker instruments, one option is to use the CompassXport
command line tool available from the vendor. For licensing reasons,
we can not provide all files required to build this Docker image.
(The LICENSE file here only refers to the Dockerfile and build instructions,
not any files provided by Bruker)

Please head over to
<https://www.bruker.com/service/support-upgrades/software-downloads/mass-spectrometry.html>
to obtain the required `CompassXport_3.0.13.1_Setup.exe` installer, and
place it into this directory prior to running e.g.

`docker build -t bruker/compassxport:3.0.13.1.1 .`

This will build with name `bruker`, the tag `compassxport` and version `3.0.13.1.1`, and read  instructions from `Dockerfile` by supplying the path to to it `.`, 

Please also take note that CompassXport is a tool unsupported by
Bruker. You are welcome to use the product, but Bruker Daltonik
Technical Support cannot provide support for the troubleshooting,
see below for an excerpt from their ReleaseNotes, and check the
installation package CompassXport_*_Setup.exe for the full information.

After building the image, the conversion can be started with e.g. See options first: `docker help run`

`docker run -v $PWD:/data bruker/compassxport:3.0.13.1.1 -multi /data/neg-MM8_1-A,1_01_376.d/ -o /data`

This will run with, [see this link for options](https://docs.docker.com/engine/reference/commandline/run/ )

- Run with with current directory $PWD mounted to /data in the container
- Run the image `/data bruker/compassxport:3.0.13.1.1` 


Excerpt from the ReleaseNotes:

````
CompassXport is not Freeware. After unpacking you will find the
License text in the ReadMe.txt file. The right to use the Software is
provided only on the condition that you ("Licensee") agree to this
Agreement.  If you do not agree to the terms of this Agreement, you
may not install the Software. However, installing the Software
indicates your acceptance of this Agreement.

CompassXport is an unsupported tool. You are welcome to use the
product, but Bruker Daltonik Technical Support cannot provide support
for the troubleshooting of CompassXport. We cannot guarantee that
we'll be able to respond to all requests and fix all
issues. Nevertheless, if you ever get into difficulties using
CompassXport you may find helpful information in an FAQ document
provided on our CompassXport download site.

CompassXport is a 'raw data' export tool, and supports 
different XML formats.

Export is currently provided for the following Bruker Daltonics MS raw data
formats:

- analysis.baf (instrument families: APEX, micrOTOF, micOTOF-Q, ...)
- analysis.yep (esquire instrument family)
- AutoXecute run for LCMaldi (instrument family: autoFlex, ultraFlex, ...)
- fid files (flex instrument family)

````
