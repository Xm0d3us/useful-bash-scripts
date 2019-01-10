# Useful Bash Scripts

Some bash scripts I have written that make my life a little easier. 

## Overview

* [__csview__](#csview) - View a csv file in less.
* [__manx__](#manx) - Browse a man page using the section headers.
* [__wd__](#wd) - Set and clear a "Working Directory" so that new terminals open to your current project.
* [__nasm2shell__](#nasm2shell) - Extract shellcode from a NASM assembly file in a C-friendly format.

## Details

### csview

__Summary:__ View an unformatted CSV file cleanly in less.

__Usage:__
- As a standalone: `$ csview somefile.csv`
- In a pipe: `$ cat somefile.csv | csview`


### manx
__Summary:__ Rather than view a large man page all at once, break it up by section headers for easier browsing.

__Usage:__ `$ manx somepage`

You will then be shown all of the section headers in the requested man page and an associated index for each. Simply select the index of the section header you want to view and press enter. Upon leaving the less interface you will be returned to the index selection. To exit simply provide empty input or press ctrl+c.

### wd

__Summary:__ Quickly set a given directory as your "Working Directory". Once set, any subsequently opened terminals will automatically navigate to the given directory. (Note: This requires the addition of a few lines to your .bashrc file. See below for more details).

__Usage:__ 
- To set the working directory: `$ wd set` or `$ wd s`. This will set the working directory to the current directory.
- To clear the working directory: `$ wd clear` or `$ wd c`
- To print the current working directory: `$ wd`

__Setup:__ In order for newly opened terminals to navigate to the working directory, the following lines must be added to your .bashrc file:

	
	if [ -e "/tmp/.working_dir" ]; then
    	if [ "$(cat /tmp/.working_dir)" != "" ]; then
    	    cd $(cat /tmp/.working_dir); 
    	fi
	fi
    
### nasm2shell

__Summary:__ Given a assembly file written in the NASM format, assemble it and extract the hex as well-formatted strings that play nice with C.

__Usage:__ `nasm2shell somefile.asm`

