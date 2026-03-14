<<<<<<< HEAD
# SVN Archive

## Pruning History

WARNING: this corrupts your database. However, the goal is to only corrupt the revisions before a given revision and maintain the integrity of all revisions after the given revision. Of course, before you do this we dump the revisions that will be corrupted.

## Archive Format

Options:
1. We keep incrementally dumping versions. The whole history must be restored as a whole this way.
1. We export the early revision and incrementally dump versions to the later version. This way each revision range can be independently restored; either the whole history through the incremental dumps (ignoring the exports), or the range can form a new history by loading the export and then its incremental dumps. This allows for the viewing of a partial history without requiring the whole to be restored.
1. We backup (non-native mechanism) the files we intend to delete such that they can be copied back without SVN noticing (and therefore they hold integrity)...but this seems like a bad idea.

## Thanks

Thank you to [Philipp's Tech Blog](https://blog.heckel.io/2011/02/01/altering-old-svn-revisions-removing-confidental-data-from-subversion-repository/) for describing corruptable steps that have insight into how revisions are stored on disk.
=======
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
>>>>>>> f8d0c7f (initial version)

