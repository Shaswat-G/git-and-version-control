Q. Why we need a version control system?
A. Tracking changes in project files overtime (time-stamped history) and collaborating with others (merging work and resolving conflicts).

Q. 2 types of Version control system?
A. Central (single point of failure like subversion and team foundation server, have to wait till it comes online) vs Distributed (everyone has a copy, like git and mercurial, snapshots are locally stored, and can be sync with each other on a network)

Q. Git usage?
A. CLI vs GUI (GitKraken - crossplatform and beautiful, sourcetree) vs IDE based (extensions in VS code like GitLens).
GUIs always have limitations - there is only so much you can do with buttons, scroll bards, graphs, etc. CLI allows fine-grained customized control.
Since everything is ultimately based on CLI learning CLI is much better for developing conceptual clarity and then you can use these concepts for using GUI tools
that others in your team / project / company use.

Installing Git:
Headover to git-scm.com/donwloads install for OS distro.
command : git --version

Git configuration Settings:
Specify name, email, default editor and line endings. By default git uses vim (scary!)
3 levels : system (all users), global (all repos of the user), local (current repo)

git config --global user.name "your_name"
git config --global user.email "your_email@email.com"

Install VS Code and add it to your path.
git config --global core.editor "code --wait"
The wait flag tells the terminal window to wait until we close the VS code instance.

git config --global -e
(Open config settings in vs code)

EOL:
In windows eol are marked with special characters carriage return (\r) and line feed (\n).
For MAC/ Linux, only line feed (\n). We have to manage this properly.

Set to true for windows users to remove \r when pushing, and add \r while pulling.
Set to input for Mac/Linux.
git config --global core.autocrlf

all documentation can be found on git-scm.com/docs

