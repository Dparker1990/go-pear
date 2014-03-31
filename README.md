## Welcome to Pear

Pear is command line utility used while pairing to ensure that each programmer is reflected in the git commits. Pear is inspired by [Hitch](https://github.com/therubymug/hitch).

## Installing Pear

We intend for this program to be installed via the OS specific distributions systems like HomeBrew and apt-get.

Until then, either download the latest release from github, or if you have the Go toolchain available use:

	$ go build -o pear

to compile the binary.

## Using Pear
### Changing Pairs

	$ pear chriserin derekparker

When prompted, enter the developer's full name. This changes the local git configuration (configuration per git repository).

### Checking Pairs

	$ pear

Pear with no arguments will let you know what programmers are configured with git.

### So you just want to work alone

	$ pear chriserin

Will change the git configuration to use just your id.

### So you like giving credit

	$ pear chriserin derekparker briandunn jackchristenson jonallured andrewdennis joshdavey

Will let you setup your git configuration to reflect all the programmers that have contributed to a commit.

### Changing Group/Email (Not yet implemented)

	$ pear --email dev@hashrocket.com

OR

	$ pear chriserin derekparker --email dev@hashrocket.com

Will configure the email associated with commits, the programmers involved will be listed as plus delimited metadata in the email address, like:

	dev+chriserin+derekparker@hashrocket.com

### Changing Pairs globally (Not yet implemented)

	$ pear --global chriserin derek parker.

Will configure git globally so that the contributing programmers will be credited in commits across all projects and repositories.

## How Pear works

Pear works by changing your local git configuration, the configuration for a specific repository. Pear stores the full name of each developer in the ~/.pearrc so that a programmer will only be prompted once for his/her full name.

If your workflow or your organization's workflow requires that the git author and git committer for commits should differ, you can change the following environment variables:

	GIT_COMMITTER_NAME

and

	GIT_COMMITTER_EMAIL

These environment variables override the details provided by the git configuration. At Hashrocket, we use "Hashrocket Workstation" as the `GIT_COMMITTER_NAME` to provide a little bit more detail about where the commit is coming from.