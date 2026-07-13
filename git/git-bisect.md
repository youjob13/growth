# When to use?
We should use [`git bisect start`](https://git-scm.com/docs/git-bisect) when we want identify commit in which we introduce a bug.
Looking your old commits one-by-one this is the real example of O(n^2) search.

It uses binary search to find the bad commit introduced a bug.
