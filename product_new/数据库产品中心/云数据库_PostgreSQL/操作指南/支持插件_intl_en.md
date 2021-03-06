TencentDB for PostgreSQL supports creating custom extensions (`create extension pluginName`). The following extensions are supported (some of them are no longer supported in PostgreSQL 10 because of its more powerful features):

| Extension                                                  | 9.3.5    | 9.5.4    | 10.4     |
| ------------------------------------------------------------ | -------- | -------- | -------- |
| btree_gin                                                    | &#10003; | &#10003; | &#10003; |
| btree_gist                                                   | &#10003; | &#10003; | &#10003; |
| chkpass                                                      | &#10003; | &#10003; | &#10003; |
| citext                                                       | &#10003; | &#10003; | &#10003; |
| cube                                                         | &#10003; | &#10003; | &#10003; |
| dict_int                                                     | &#10003; | &#10003; | &#10003; |
| earthdistance                                                | &#10003; | &#10003; | &#10003; |
| [postgres_fdw](https://intl.cloud.tencent.com/document/product/409/18706) | &#10003; | &#10003; | × |
| [mysql_fdw](https://intl.cloud.tencent.com/document/product/409/18706 ) | &#10003; | &#10003; | × |
| [cos_fdw](https://intl.cloud.tencent.com/document/product/409/18706 ) | &#10003; | &#10003; | × |
| fuzzystrmatch                                                | &#10003; | &#10003; | &#10003; |
| hstore                                                       | &#10003; | &#10003; | &#10003; |
| intagg                                                       | &#10003; | &#10003; | &#10003; |
| intarray                                                     | &#10003; | &#10003; | &#10003; |
| isn                                                          | &#10003; | &#10003; | &#10003; |
| jsonbx                                                       | ×        | &#10003; | ×        |
| ltree                                                        | &#10003; | &#10003; | &#10003; |
| pg_hint_plan                                                 | &#10003; | &#10003; | ×        |
| pg_prewarm                                                   | ×        | &#10003; | &#10003; |
| pg_stat_statements                                           | &#10003; | &#10003; | &#10003; |
| pg_trgm                                                      | &#10003; | &#10003; | &#10003; |
| pgcrypto                                                     | &#10003; | &#10003; | &#10003; |
| pgrouting                                                    | &#10003; | &#10003; | &#10003; |
| pgrowlocks                                                   | &#10003; | &#10003; | &#10003; |
| pl/perl                                                      | &#10003; | &#10003; | &#10003; |
| pl/pgsql                                                     | &#10003; | &#10003; | &#10003; |
| pl/tcl                                                       | &#10003; | &#10003; | &#10003; |
| plcoffee                                                     | &#10003; | &#10003; | &#10003; |
| plls                                                         | &#10003; | &#10003; | &#10003; |
| plv8                                                         | &#10003; | &#10003; | &#10003; |
| postgis                                                      | &#10003; | &#10003; | &#10003; |
| postgis_tiger_geocoder                                       | &#10003; | &#10003; | &#10003; |
| postgres_fdw                                                 | &#10003; | &#10003; | &#10003; |
| sslinfo                                                      | &#10003; | &#10003; | &#10003; |
| tablefunc                                                    | &#10003; | &#10003; | &#10003; |
| tsearch2                                                     | &#10003; | &#10003; | ×        |
| unaccent                                                     | &#10003; | &#10003; | &#10003; |
| uuid-ossp                                                    | &#10003; | &#10003; | &#10003; |
| zhparser                                                     | &#10003; | &#10003; | &#10003; |
