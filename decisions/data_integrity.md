**Over what threshold do we deem it valuable work to clean up inconsistent data?**

* Always valuable!
* We lean towards backfilling when it’s clear what the existing data should be
* Existing data
  * Nullified foreign keys due to some kind of delete error / logic
    * Packages with null packageable_id, for example, and / or packages that point to non-existent packageable.
* Adding new columns / data with inconsistent data
* Add sane(not null) database constraints when possible
