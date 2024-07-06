---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🦊 Restrição de check

```plsql
CREATE EXTENSION btree_gist;

create function tsrange_immutable(timestamp) returns tsrange immutable language sql as
$$select tsrange($1, $1 + interval '20 seconds')$$;

ALTER TABLE awards_payments_batch
ADD EXCLUDE USING GIST (
    company_id WITH =,
    tsrange_immutable(created_at) WITH &&
);
```
