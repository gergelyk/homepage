# git-rsync

<p align="right">
<a href="https://github.com/gergelyk/git-rsync/tree/master/doc"><img src="/assets/book.svg"/></a>
<a href="https://github.com/gergelyk/git-rsync"><img src="/assets/github.svg"/></a>
<a href="https://github.com/gergelyk/git-rsync/releases"><img src="/assets/app.svg"/></a>
</p>



Extends git with ability of handling large files.

What differs git-rsync from other solutions is that large files are not bundled to the commits, but rather to the tags, or user-defined names. Large files are stored under original names, which makes it easy to restore them manually if such need arises. git-rsynch is distributed as compliled executable, which significantly reduces number of dependencies. Finally git-rsync can be used right away, without any configuration. At the same time, tool is configurable to reflect everyone's needs.

## Example

Let's consider simple example where we use only local repository for private purposes.

We start from creating git repository:

```sh
$ mkdir repo
$ cd repo
$ git init
```

Since we plan to use `git-rsync`, we should invoke `init` command which will create `storage` directory and `.gitrsync` file.

```sh
$ git rsync init
```

`storage` directory will be used to store large files (in subdirectories). By default it goes to `.git` directory.

`.gitrsync` defines files to be exported by `git-rsync` command. It should be placed in the top directory of the local repo.

Let's instruct git to consider all .exe and .jpg files in the top directory as large files. They will be handled by git-rsync, but ignored by git itself.

```sh
$ echo "*.exe" > .gitrsync
$ echo "*.jpg" >> .gitrsync
$ cp .gitrsync .gitignore
```

Now it's time to add some files of the project and commit them to the repo.

```sh
$ touch main.cpp
$ touch splash.jpg
$ touch app.exe
$ git ci -m "first release"
```

In order to export large files, we need to use `git-rsync push command`, but first let's create a tag, so `git-rsync` knows which sub-directory in the storage should be used.


```sh
$ git tag 1.0.0
$ git rsync push
```

We can verify if files have been exported:

```sh
$ ls .git/storage
1.0.0
$ ls .git/storage/1.0.0
app.exe splash.jpg
```

Now we can clean the repo from the large files and check if `git-rsync` can restore them:

```sh
$ git clean -dfx
$ ls
main.cpp
$ git rsync pull
$ ls
app.exe  main.cpp  splash.jpg
```

Note that `git-rsync` can create storage in remote repo user defined directory. For more information refer to the Manual.
