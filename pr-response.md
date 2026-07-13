# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename
**What I did:** Renamed `save_to_watchlist()` to `add_to_watchlist()` in `services/watchlist_service.py` and updated the import and call site in `routes/watchlist/watchlist.py`. This matches the existing `add_to_collection()` naming convention.

**How I verified:** Searched the repository for `save_to_watchlist` and confirmed no source references remained. I also ran `python -m pytest`, and all 4 existing tests passed.

## Comment 2 — Deduplication
**What I did:** Added a lookup for an existing `WatchlistEntry` with the same `user_id` and `film_id`. If one exists, `add_to_watchlist()` raises `AlreadyInWatchlistError` instead of creating a duplicate row. This follows the pattern used by `add_to_collection()`.

**How I verified:** Compared the implementation with `add_to_collection()` in `services/collection_service.py` and ran `python -m pytest`.

## Comment 3 — Missing test
**What I did:** Added tests/test_watchlist.py with a missing-film test for add_to_watchlist(), using the collection missing-film test as the model.
**How I verified:** I used pytest tests/test_watchlist.py -v and pytest tests/ -v to verify the new test file and the broader test suite.

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
