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

