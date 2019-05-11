# qeBinaries

This repo is used to store Windows's msi files and Linux (CentOS) rpm files.
These may be used to install EPICS Qt framework and designer together with support
libraries, with minimal fuss.

NOTE: This repository has been re-initialised and converted to a Large File
Storage (LFS) repository. I suggest a fresh git clone.

     git clone https://github.com/qtepics/qeBinaries.git

Using this command, the LFS nature of the msi and rpm files is hidden from the
user.


## msi files

For the msi files, just double click on the file in a Windows 7 or 10 environment.
We have not tried Windows 8, but expect that would be okay.
Feedback re Windows 8, success or failure, would be good.
For Windows XP, there are run time issues post installation.

As part of the install, two desktop icons are created - one for designer and one
for qegui, and environment variables created: QT_PLUGIN_PATH and QE_ARCHIVE_LIST.
The later is set up for use within the Australian Synchrotron and will have to
be modified to suit your facility.

NOTE: Before installing a new version, you __will__ have to uninstall the existing
version.


## rpm files

As root (or using sudo) run the following (note this is using 3.7.1 as example)

    rpm -hvi  epicsQt-3.7.1-el7.x86_64.rpm

The installed package is named epicsQt-3.7.1-el7.x86_64, and may be removed by running:

    rpm -e epicsQt-3.7.1-el7.x86_64

The package includes qegui and designer and support libraries (QT, EPICS, QWT etc.)
but does not (currently) include caRepeater.

The majority of files are installed in __/opt/australian_synchrotron/epicsQt/__
and two wrapper scripts are also installed in __/usr/local/bin/__.
These are:

    /usr/local/bin/designer
    /usr/local/bin/qegui

These scripts are simple wrapper scripts to set up the required environment
variables in order to to run qegui and designer.

__Note:__ they do not clear QT_PLUGIN_PATH, so other plugins on the path are still
available, however they may be incompatible with the package plugins and
may cause issues.
Consider un-setting QT_PLUGIN_PATH before calling these scripts, or using them
as the basis for your own scripts.
