* General hg/git hints
  * https://github.com/sympy/sympy/wiki/Git-hg-rosetta-stone
* Separating out a directory from a repo into its own repo
E.g., separate out myhg/raccounts into its own repo, with the files from myhg/raccounts at the top-level (instead of under raccounts)
  1. Create ~/new-raccounts-repo.filemap
    ```
    $ cat ~/new-raccounts-repo.filemap 
    include raccounts
    rename raccounts .
    ```
  2. Run this to create the new repo:
    ```
    hg convert ~/myhg/ ~/new-raccounts-repo --filemap ~/new-raccounts-repo.filemap
    ```
    (Then run "hg checkout" to see the files in the new repo.)

You can also remove that directory from the old repo with a different filemap.  See http://510x.se/notes/posts/Splitting_a_Mercurial_repository_while_keeping_relevant_history/

* Importing an entire repo into Git
```
$ git init new-git-repo
$ cd new-git-repo
$ ~/git/fast-export/hg-fast-export.sh -r /path/to/Mercurial-repo-to-import
$ git checkout HEAD
```

See answer on using fast-export at https://stackoverflow.com/questions/16037787/convert-mercurial-project-to-git
