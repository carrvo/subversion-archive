# subversion-archive

Archiving solution for [subversion](https://subversion.apache.org/).

## Setup

You need to configure your SVN repository with the hook.

Note the following requirements:
- `/path/to/svn-repo/` *MUST* end in a slash (`/`) to ensure that it is a directory

1. Clone
1. Run `make debian-package-dependencies` to install dependent *build* Debian packages
1. Run `make debian-package` to build package locally
1. Run `dpkg -i package/subversion-archive_X.X.X_all.deb` to install package locally
- [SVN](https://subversion.apache.org/)
1. add the hook to the repository
    ```
    add-subversion-archive /path/to/svn-repo/ limit-history
    ```

## Options

### Limit History

This will **REMOVE** all but the last N commits.
Subversion will continue to operate as expected as log as
you do not try to access any history older than this.

## License

Copyright 2024 by carrvo

License: TBD

