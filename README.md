# 安装mysql-8.0.18
1.下载，https://dev.mysql.com/downloads/mysql/  
2.解压到指定目录，在D:\EnvRun\mysql-8.0.18-winx64目录下新建my.ini  
```
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录 windows 正斜杠单个 反斜杠要加双
basedir=/
# 设置mysql数据库的数据的存放目录
datadir=\\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。
max_connect_errors=10
# 服务端使用的字符集默认为utf8mb4
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
```
3.cmd进入bin文件夹下，生成密码
```
mysqld --initialize --user=root --console
```
4.安装为windows服务
```
mysqld install
```
5.启动
```
net start mysql
```
6.登录
```
mysql -u root -p
```
7.修改密码
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH MYSQL_NATIVE_PASSWORD BY '新密码';
```
8.刷新权限
```
FLUSH PRIVILEGES;
```
注意事项：以管理员权限启动cmd，否则报错。

## 导出默认配置 
```
running: mysqladmin variables
not running: mysqld --verbose --help >> C:\\mysqld.txt
```
## 附上默认配置 mysql-8.0.32
```
abort-slave-event-count                                      0
activate-all-roles-on-login                                  FALSE
admin-address                                                (No default value)
admin-port                                                   33062
admin-ssl                                                    TRUE
admin-ssl-ca                                                 (No default value)
admin-ssl-capath                                             (No default value)
admin-ssl-cert                                               (No default value)
admin-ssl-cipher                                             (No default value)
admin-ssl-crl                                                (No default value)
admin-ssl-crlpath                                            (No default value)
admin-ssl-key                                                (No default value)
admin-tls-ciphersuites                                       (No default value)
admin-tls-version                                            TLSv1.2,TLSv1.3
allow-suspicious-udfs                                        FALSE
archive                                                      ON
authentication-policy                                        *,,
auto-generate-certs                                          TRUE
auto-increment-increment                                     1
auto-increment-offset                                        1
autocommit                                                   TRUE
automatic-sp-privileges                                      TRUE
avoid-temporal-upgrade                                       FALSE
back-log                                                     151
basedir                                                      D:\Software\mysql-8.0.32-winx64\
big-tables                                                   FALSE
bind-address                                                 *
binlog-cache-size                                            32768
binlog-checksum                                              CRC32
binlog-direct-non-transactional-updates                      FALSE
binlog-encryption                                            FALSE
binlog-error-action                                          ABORT_SERVER
binlog-expire-logs-auto-purge                                TRUE
binlog-expire-logs-seconds                                   2592000
binlog-format                                                ROW
binlog-group-commit-sync-delay                               0
binlog-group-commit-sync-no-delay-count                      0
binlog-gtid-simple-recovery                                  TRUE
binlog-max-flush-queue-time                                  0
binlog-order-commits                                         TRUE
binlog-rotate-encryption-master-key-at-startup               FALSE
binlog-row-event-max-size                                    8192
binlog-row-image                                             FULL
binlog-row-metadata                                          MINIMAL
binlog-row-value-options                                     
binlog-rows-query-log-events                                 FALSE
binlog-stmt-cache-size                                       32768
binlog-transaction-compression                               FALSE
binlog-transaction-compression-level-zstd                    3
binlog-transaction-dependency-history-size                   25000
binlog-transaction-dependency-tracking                       COMMIT_ORDER
blackhole                                                    ON
block-encryption-mode                                        aes-128-ecb
bulk-insert-buffer-size                                      8388608
caching-sha2-password-auto-generate-rsa-keys                 TRUE
caching-sha2-password-digest-rounds                          5000
caching-sha2-password-private-key-path                       private_key.pem
caching-sha2-password-public-key-path                        public_key.pem
character-set-client-handshake                               TRUE
character-set-filesystem                                     binary
character-set-server                                         utf8mb4
character-sets-dir                                           D:\Software\mysql-8.0.32-winx64\share\charsets\
check-proxy-users                                            FALSE
chroot                                                       (No default value)
collation-server                                             utf8mb4_0900_ai_ci
completion-type                                              NO_CHAIN
concurrent-insert                                            AUTO
connect-timeout                                              10
connection-memory-chunk-size                                 8912
connection-memory-limit                                      18446744073709551615
console                                                      FALSE
create-admin-listener-thread                                 FALSE
cte-max-recursion-depth                                      1000
datadir                                                      D:\Software\mysql-8.0.32-winx64\data\
default-authentication-plugin                                caching_sha2_password
default-password-lifetime                                    0
default-storage-engine                                       InnoDB
default-table-encryption                                     FALSE
default-time-zone                                            (No default value)
default-tmp-storage-engine                                   InnoDB
default-week-format                                          0
delay-key-write                                              ON
delayed-insert-limit                                         100
delayed-insert-timeout                                       300
delayed-queue-size                                           1000
disabled-storage-engines                                     
disconnect-on-expired-password                               TRUE
disconnect-slave-event-count                                 0
div-precision-increment                                      4
end-markers-in-json                                          FALSE
enforce-gtid-consistency                                     FALSE
eq-range-index-dive-limit                                    200
event-scheduler                                              ON
expire-logs-days                                             0
explain-format                                               TRADITIONAL
explicit-defaults-for-timestamp                              TRUE
external-locking                                             FALSE
federated                                                    OFF
flush                                                        FALSE
flush-time                                                   0
ft-boolean-syntax                                            + -><()~*:""&|
ft-max-word-len                                              84
ft-min-word-len                                              4
ft-query-expansion-limit                                     20
ft-stopword-file                                             (No default value)
gdb                                                          FALSE
general-log                                                  FALSE
general-log-file                                             D:\Software\mysql-8.0.32-winx64\data\phascolarctos.log
generated-random-password-length                             20
global-connection-memory-limit                               18446744073709551615
global-connection-memory-tracking                            FALSE
group-concat-max-len                                         1024
group-replication-consistency                                EVENTUAL
gtid-executed-compression-period                             0
gtid-mode                                                    OFF
help                                                         TRUE
histogram-generation-max-mem-size                            20000000
host-cache-size                                              279
information-schema-stats-expiry                              86400
init-connect                                                 
init-file                                                    (No default value)
init-replica                                                 
init-slave                                                   
initialize                                                   FALSE
initialize-insecure                                          FALSE
innodb-adaptive-flushing                                     TRUE
innodb-adaptive-flushing-lwm                                 10
innodb-adaptive-hash-index                                   TRUE
innodb-adaptive-hash-index-parts                             8
innodb-adaptive-max-sleep-delay                              150000
innodb-api-bk-commit-interval                                5
innodb-api-disable-rowlock                                   FALSE
innodb-api-enable-binlog                                     FALSE
innodb-api-enable-mdl                                        FALSE
innodb-api-trx-level                                         0
innodb-autoextend-increment                                  64
innodb-autoinc-lock-mode                                     2
innodb-buffer-pool-chunk-size                                134217728
innodb-buffer-pool-dump-at-shutdown                          TRUE
innodb-buffer-pool-dump-now                                  FALSE
innodb-buffer-pool-dump-pct                                  25
innodb-buffer-pool-filename                                  ib_buffer_pool
innodb-buffer-pool-in-core-file                              TRUE
innodb-buffer-pool-instances                                 0
innodb-buffer-pool-load-abort                                FALSE
innodb-buffer-pool-load-at-startup                           TRUE
innodb-buffer-pool-load-now                                  FALSE
innodb-buffer-pool-size                                      134217728
innodb-change-buffer-max-size                                25
innodb-change-buffering                                      all
innodb-checksum-algorithm                                    crc32
innodb-cmp-per-index-enabled                                 FALSE
innodb-commit-concurrency                                    0
innodb-compression-failure-threshold-pct                     5
innodb-compression-level                                     6
innodb-compression-pad-pct-max                               50
innodb-concurrency-tickets                                   5000
innodb-data-file-path                                        ibdata1:12M:autoextend
innodb-data-home-dir                                         (No default value)
innodb-ddl-buffer-size                                       1048576
innodb-ddl-threads                                           4
innodb-deadlock-detect                                       TRUE
innodb-dedicated-server                                      FALSE
innodb-default-row-format                                    dynamic
innodb-directories                                           (No default value)
innodb-disable-sort-file-cache                               FALSE
innodb-doublewrite                                           ON
innodb-doublewrite-batch-size                                0
innodb-doublewrite-dir                                       (No default value)
innodb-doublewrite-files                                     0
innodb-doublewrite-pages                                     0
innodb-extend-and-initialize                                 TRUE
innodb-fast-shutdown                                         1
innodb-file-per-table                                        TRUE
innodb-fill-factor                                           100
innodb-flush-log-at-timeout                                  1
innodb-flush-log-at-trx-commit                               1
innodb-flush-method                                          unbuffered
innodb-flush-neighbors                                       0
innodb-flush-sync                                            TRUE
innodb-flushing-avg-loops                                    30
innodb-force-load-corrupted                                  FALSE
innodb-force-recovery                                        0
innodb-fsync-threshold                                       0
innodb-ft-aux-table                                          (No default value)
innodb-ft-cache-size                                         8000000
innodb-ft-enable-diag-print                                  FALSE
innodb-ft-enable-stopword                                    TRUE
innodb-ft-max-token-size                                     84
innodb-ft-min-token-size                                     3
innodb-ft-num-word-optimize                                  2000
innodb-ft-result-cache-limit                                 2000000000
innodb-ft-server-stopword-table                              (No default value)
innodb-ft-sort-pll-degree                                    2
innodb-ft-total-cache-size                                   640000000
innodb-ft-user-stopword-table                                (No default value)
innodb-idle-flush-pct                                        100
innodb-io-capacity                                           200
innodb-io-capacity-max                                       4294967295
innodb-lock-wait-timeout                                     50
innodb-log-buffer-size                                       16777216
innodb-log-checksums                                         TRUE
innodb-log-compressed-pages                                  TRUE
innodb-log-file-size                                         50331648
innodb-log-files-in-group                                    2
innodb-log-group-home-dir                                    (No default value)
innodb-log-spin-cpu-abs-lwm                                  80
innodb-log-spin-cpu-pct-hwm                                  50
innodb-log-wait-for-flush-spin-hwm                           400
innodb-log-write-ahead-size                                  8192
innodb-log-writer-threads                                    TRUE
innodb-lru-scan-depth                                        1024
innodb-max-dirty-pages-pct                                   90
innodb-max-dirty-pages-pct-lwm                               10
innodb-max-purge-lag                                         0
innodb-max-purge-lag-delay                                   0
innodb-max-undo-log-size                                     1073741824
innodb-monitor-disable                                       (No default value)
innodb-monitor-enable                                        (No default value)
innodb-monitor-reset                                         (No default value)
innodb-monitor-reset-all                                     (No default value)
innodb-old-blocks-pct                                        37
innodb-old-blocks-time                                       1000
innodb-online-alter-log-max-size                             134217728
innodb-open-files                                            0
innodb-optimize-fulltext-only                                FALSE
innodb-page-cleaners                                         4
innodb-page-size                                             16384
innodb-parallel-read-threads                                 4
innodb-print-all-deadlocks                                   FALSE
innodb-print-ddl-logs                                        FALSE
innodb-purge-batch-size                                      300
innodb-purge-rseg-truncate-frequency                         128
innodb-purge-threads                                         4
innodb-random-read-ahead                                     FALSE
innodb-read-ahead-threshold                                  56
innodb-read-io-threads                                       4
innodb-read-only                                             FALSE
innodb-redo-log-archive-dirs                                 (No default value)
innodb-redo-log-capacity                                     104857600
innodb-redo-log-encrypt                                      FALSE
innodb-replication-delay                                     0
innodb-rollback-on-timeout                                   FALSE
innodb-rollback-segments                                     128
innodb-segment-reserve-factor                                12.5
innodb-sort-buffer-size                                      1048576
innodb-spin-wait-delay                                       6
innodb-spin-wait-pause-multiplier                            50
innodb-stats-auto-recalc                                     TRUE
innodb-stats-include-delete-marked                           FALSE
innodb-stats-method                                          nulls_equal
innodb-stats-on-metadata                                     FALSE
innodb-stats-persistent                                      TRUE
innodb-stats-persistent-sample-pages                         20
innodb-stats-transient-sample-pages                          8
innodb-status-file                                           FALSE
innodb-status-output                                         FALSE
innodb-status-output-locks                                   FALSE
innodb-strict-mode                                           TRUE
innodb-sync-array-size                                       1
innodb-sync-spin-loops                                       30
innodb-table-locks                                           TRUE
innodb-temp-data-file-path                                   ibtmp1:12M:autoextend
innodb-temp-tablespaces-dir                                  (No default value)
innodb-thread-concurrency                                    0
innodb-thread-sleep-delay                                    10000
innodb-tmpdir                                                (No default value)
innodb-undo-directory                                        (No default value)
innodb-undo-log-encrypt                                      FALSE
innodb-undo-log-truncate                                     TRUE
innodb-undo-tablespaces                                      2
innodb-use-fdatasync                                         FALSE
innodb-use-native-aio                                        TRUE
innodb-validate-tablespace-paths                             TRUE
innodb-write-io-threads                                      4
interactive-timeout                                          28800
internal-tmp-mem-storage-engine                              TempTable
join-buffer-size                                             262144
keep-files-on-create                                         FALSE
key-buffer-size                                              8388608
key-cache-age-threshold                                      300
key-cache-block-size                                         1024
key-cache-division-limit                                     100
keyring-migration-destination                                (No default value)
keyring-migration-host                                       (No default value)
keyring-migration-port                                       0
keyring-migration-socket                                     (No default value)
keyring-migration-source                                     (No default value)
keyring-migration-to-component                               FALSE
keyring-migration-user                                       (No default value)
language                                                     D:\Software\mysql-8.0.32-winx64\share\
lc-messages                                                  en_US
lc-messages-dir                                              D:\Software\mysql-8.0.32-winx64\share\
lc-time-names                                                en_US
local-infile                                                 FALSE
lock-wait-timeout                                            31536000
log-bin                                                      binlog
log-bin-index                                                binlog.index
log-bin-trust-function-creators                              FALSE
log-bin-use-v1-row-events                                    FALSE
log-error                                                    stderr
log-error-services                                           log_filter_internal; log_sink_internal
log-error-suppression-list                                   
log-error-verbosity                                          1
log-isam                                                     myisam.log
log-output                                                   FILE
log-queries-not-using-indexes                                FALSE
log-raw                                                      FALSE
log-replica-updates                                          TRUE
log-short-format                                             FALSE
log-slave-updates                                            TRUE
log-slow-admin-statements                                    FALSE
log-slow-extra                                               FALSE
log-slow-replica-statements                                  FALSE
log-slow-slave-statements                                    FALSE
log-statements-unsafe-for-binlog                             TRUE
log-tc                                                       tc.log
log-tc-size                                                  24576
log-throttle-queries-not-using-indexes                       0
log-timestamps                                               UTC
long-query-time                                              10
low-priority-updates                                         FALSE
lower-case-table-names                                       1
mandatory-roles                                              
master-info-file                                             master.info
master-info-repository                                       TABLE
master-retry-count                                           86400
master-verify-checksum                                       FALSE
max-allowed-packet                                           67108864
max-binlog-cache-size                                        18446744073709547520
max-binlog-dump-events                                       0
max-binlog-size                                              1073741824
max-binlog-stmt-cache-size                                   18446744073709547520
max-connect-errors                                           100
max-connections                                              151
max-delayed-threads                                          20
max-digest-length                                            1024
max-error-count                                              1024
max-execution-time                                           0
max-heap-table-size                                          16777216
max-join-size                                                18446744073709551615
max-length-for-sort-data                                     4096
max-points-in-geometry                                       65536
max-prepared-stmt-count                                      16382
max-relay-log-size                                           0
max-seeks-for-key                                            4294967295
max-sort-length                                              1024
max-sp-recursion-depth                                       0
max-user-connections                                         0
max-write-lock-count                                         4294967295
memlock                                                      FALSE
min-examined-row-limit                                       0
myisam-block-size                                            1024
myisam-data-pointer-size                                     6
myisam-max-sort-file-size                                    2146435072
myisam-mmap-size                                             18446744073709551615
myisam-recover-options                                       OFF
myisam-sort-buffer-size                                      8388608
myisam-stats-method                                          nulls_unequal
myisam-use-mmap                                              FALSE
mysql-native-password-proxy-users                            FALSE
mysqlx                                                       ON
mysqlx-bind-address                                          *
mysqlx-cache-cleaner                                         ON
mysqlx-compression-algorithms                                DEFLATE_STREAM,LZ4_MESSAGE,ZSTD_STREAM
mysqlx-connect-timeout                                       30
mysqlx-deflate-default-compression-level                     3
mysqlx-deflate-max-client-compression-level                  5
mysqlx-document-id-unique-prefix                             0
mysqlx-enable-hello-notice                                   TRUE
mysqlx-idle-worker-thread-timeout                            60
mysqlx-interactive-timeout                                   28800
mysqlx-lz4-default-compression-level                         2
mysqlx-lz4-max-client-compression-level                      8
mysqlx-max-allowed-packet                                    67108864
mysqlx-max-connections                                       100
mysqlx-min-worker-threads                                    2
mysqlx-port                                                  33060
mysqlx-port-open-timeout                                     0
mysqlx-read-timeout                                          30
mysqlx-socket                                                (No default value)
mysqlx-ssl-ca                                                (No default value)
mysqlx-ssl-capath                                            (No default value)
mysqlx-ssl-cert                                              (No default value)
mysqlx-ssl-cipher                                            (No default value)
mysqlx-ssl-crl                                               (No default value)
mysqlx-ssl-crlpath                                           (No default value)
mysqlx-ssl-key                                               (No default value)
mysqlx-wait-timeout                                          28800
mysqlx-write-timeout                                         60
mysqlx-zstd-default-compression-level                        3
mysqlx-zstd-max-client-compression-level                     11
named-pipe                                                   FALSE
named-pipe-full-access-group                                 
ndb-allow-copying-alter-table                                TRUE
ndb-applier-allow-skip-epoch                                 FALSE
ndb-applier-conflict-role                                    NONE
ndb-autoincrement-prefetch-sz                                512
ndb-batch-size                                               32768
ndb-blob-read-batch-bytes                                    65536
ndb-blob-write-batch-bytes                                   65536
ndb-clear-apply-status                                       TRUE
ndb-cluster-connection-pool                                  1
ndb-cluster-connection-pool-nodeids                          (No default value)
ndb-connectstring                                            (No default value)
ndb-data-node-neighbour                                      0
ndb-default-column-format                                    FIXED
ndb-deferred-constraints                                     0
ndb-distribution                                             KEYHASH
ndb-eventbuffer-free-percent                                 20
ndb-eventbuffer-max-alloc                                    0
ndb-extra-logging                                            1
ndb-force-send                                               TRUE
ndb-fully-replicated                                         FALSE
ndb-index-stat-enable                                        TRUE
ndb-index-stat-option                                        loop_enable=1000ms,loop_idle=1000ms,loop_busy=100ms,update_batch=1,read_batch=4,idle_batch=32,check_batch=8,check_delay=10m,delete_batch=8,clean_delay=1m,error_batch=4,error_delay=1m,evict_batch=8,evict_delay=1m,cache_limit=32M,cache_lowpct=90,zero_total=0
ndb-join-pushdown                                            TRUE
ndb-log-apply-status                                         FALSE
ndb-log-bin                                                  FALSE
ndb-log-binlog-index                                         TRUE
ndb-log-empty-epochs                                         FALSE
ndb-log-empty-update                                         FALSE
ndb-log-exclusive-reads                                      FALSE
ndb-log-fail-terminate                                       FALSE
ndb-log-orig                                                 FALSE
ndb-log-transaction-compression                              FALSE
ndb-log-transaction-compression-level-zstd                   3
ndb-log-transaction-id                                       FALSE
ndb-log-update-as-write                                      TRUE
ndb-log-update-minimal                                       FALSE
ndb-log-updated-only                                         TRUE
ndb-metadata-check                                           TRUE
ndb-metadata-check-interval                                  60
ndb-metadata-sync                                            FALSE
ndb-mgmd-host                                                (No default value)
ndb-nodeid                                                   0
ndb-optimization-delay                                       10
ndb-optimized-node-selection                                 3
ndb-read-backup                                              TRUE
ndb-recv-thread-activation-threshold                         8
ndb-recv-thread-cpu-mask                                     
ndb-replica-batch-size                                       2097152
ndb-replica-blob-write-batch-bytes                           2097152
ndb-report-thresh-binlog-epoch-slip                          10
ndb-report-thresh-binlog-mem-usage                           10
ndb-row-checksum                                             1
ndb-schema-dist-lock-wait-timeout                            30
ndb-schema-dist-timeout                                      120
ndb-schema-dist-upgrade-allowed                              TRUE
ndb-show-foreign-key-mock-tables                             FALSE
ndb-slave-conflict-role                                      NONE
ndb-table-no-logging                                         FALSE
ndb-table-temporary                                          FALSE
ndb-transid-mysql-connection-map                             OFF
ndb-use-copying-alter-table                                  FALSE
ndb-use-exact-count                                          FALSE
ndb-use-transactions                                         TRUE
ndb-wait-connected                                           120
ndb-wait-setup                                               120
ndbcluster                                                   OFF
ndbinfo                                                      OFF
ndbinfo-max-bytes                                            0
ndbinfo-max-rows                                             10
ndbinfo-show-hidden                                          FALSE
net-buffer-length                                            16384
net-read-timeout                                             30
net-retry-count                                              10
net-write-timeout                                            60
new                                                          FALSE
ngram                                                        ON
ngram-token-size                                             2
no-dd-upgrade                                                FALSE
no-monitor                                                   FALSE
offline-mode                                                 FALSE
old                                                          FALSE
old-alter-table                                              FALSE
old-style-user-limits                                        FALSE
open-files-limit                                             10209
optimizer-max-subgraph-pairs                                 100000
optimizer-prune-level                                        1
optimizer-search-depth                                       62
optimizer-switch                                             index_merge=on,index_merge_union=on,index_merge_sort_union=on,index_merge_intersection=on,engine_condition_pushdown=on,index_condition_pushdown=on,mrr=on,mrr_cost_based=on,block_nested_loop=on,batched_key_access=off,materialization=on,semijoin=on,loosescan=on,firstmatch=on,duplicateweedout=on,subquery_materialization_cost_based=on,use_index_extensions=on,condition_fanout_filter=on,derived_merge=on,use_invisible_indexes=off,skip_scan=on,hash_join=on,subquery_to_derived=off,prefer_ordering_index=on,hypergraph_optimizer=off,derived_condition_pushdown=on
optimizer-trace                                              
optimizer-trace-features                                     greedy_search=on,range_optimizer=on,dynamic_range=on,repeated_subselect=on
optimizer-trace-limit                                        1
optimizer-trace-max-mem-size                                 1048576
optimizer-trace-offset                                       -1
parser-max-mem-size                                          18446744073709551615
partial-revokes                                              FALSE
password-history                                             0
password-require-current                                     FALSE
password-reuse-interval                                      0
performance-schema                                           TRUE
performance-schema-accounts-size                             -1
performance-schema-consumer-events-stages-current            FALSE
performance-schema-consumer-events-stages-history            FALSE
performance-schema-consumer-events-stages-history-long       FALSE
performance-schema-consumer-events-statements-cpu            FALSE
performance-schema-consumer-events-statements-current        TRUE
performance-schema-consumer-events-statements-history        TRUE
performance-schema-consumer-events-statements-history-long   FALSE
performance-schema-consumer-events-transactions-current      TRUE
performance-schema-consumer-events-transactions-history      TRUE
performance-schema-consumer-events-transactions-history-long FALSE
performance-schema-consumer-events-waits-current             FALSE
performance-schema-consumer-events-waits-history             FALSE
performance-schema-consumer-events-waits-history-long        FALSE
performance-schema-consumer-global-instrumentation           TRUE
performance-schema-consumer-statements-digest                TRUE
performance-schema-consumer-thread-instrumentation           TRUE
performance-schema-digests-size                              -1
performance-schema-error-size                                5242
performance-schema-events-stages-history-long-size           -1
performance-schema-events-stages-history-size                -1
performance-schema-events-statements-history-long-size       -1
performance-schema-events-statements-history-size            -1
performance-schema-events-transactions-history-long-size     -1
performance-schema-events-transactions-history-size          -1
performance-schema-events-waits-history-long-size            -1
performance-schema-events-waits-history-size                 -1
performance-schema-hosts-size                                -1
performance-schema-instrument                                
performance-schema-max-cond-classes                          150
performance-schema-max-cond-instances                        -1
performance-schema-max-digest-length                         1024
performance-schema-max-digest-sample-age                     60
performance-schema-max-file-classes                          80
performance-schema-max-file-handles                          32768
performance-schema-max-file-instances                        -1
performance-schema-max-index-stat                            -1
performance-schema-max-memory-classes                        450
performance-schema-max-metadata-locks                        -1
performance-schema-max-mutex-classes                         350
performance-schema-max-mutex-instances                       -1
performance-schema-max-prepared-statements-instances         -1
performance-schema-max-program-instances                     -1
performance-schema-max-rwlock-classes                        60
performance-schema-max-rwlock-instances                      -1
performance-schema-max-socket-classes                        10
performance-schema-max-socket-instances                      -1
performance-schema-max-sql-text-length                       1024
performance-schema-max-stage-classes                         175
performance-schema-max-statement-classes                     219
performance-schema-max-statement-stack                       10
performance-schema-max-table-handles                         -1
performance-schema-max-table-instances                       -1
performance-schema-max-table-lock-stat                       -1
performance-schema-max-thread-classes                        100
performance-schema-max-thread-instances                      -1
performance-schema-session-connect-attrs-size                -1
performance-schema-setup-actors-size                         -1
performance-schema-setup-objects-size                        -1
performance-schema-show-processlist                          FALSE
performance-schema-users-size                                -1
persist-only-admin-x509-subject                              
persist-sensitive-variables-in-plaintext                     TRUE
persisted-globals-load                                       TRUE
pid-file                                                     D:\Software\mysql-8.0.32-winx64\data\phascolarctos.pid
plugin-dir                                                   D:\Software\mysql-8.0.32-winx64\lib\plugin\
port                                                         3306
port-open-timeout                                            0
preload-buffer-size                                          32768
print-identified-with-as-hex                                 FALSE
profiling-history-size                                       15
protocol-compression-algorithms                              zlib,zstd,uncompressed
query-alloc-block-size                                       8192
query-prealloc-size                                          8192
range-alloc-block-size                                       4096
range-optimizer-max-mem-size                                 8388608
read-buffer-size                                             131072
read-only                                                    FALSE
read-rnd-buffer-size                                         262144
regexp-stack-limit                                           8000000
regexp-time-limit                                            32
relay-log                                                    phascolarctos-relay-bin
relay-log-index                                              phascolarctos-relay-bin.index
relay-log-info-file                                          relay-log.info
relay-log-info-repository                                    TABLE
relay-log-purge                                              TRUE
relay-log-recovery                                           FALSE
relay-log-space-limit                                        0
replica-allow-batching                                       TRUE
replica-checkpoint-group                                     512
replica-checkpoint-period                                    300
replica-compressed-protocol                                  FALSE
replica-exec-mode                                            STRICT
replica-load-tmpdir                                          C:\Users\docming\AppData\Local\Temp
replica-max-allowed-packet                                   1073741824
replica-net-timeout                                          60
replica-parallel-type                                        LOGICAL_CLOCK
replica-parallel-workers                                     4
replica-pending-jobs-size-max                                134217728
replica-preserve-commit-order                                TRUE
replica-skip-errors                                          (No default value)
replica-sql-verify-checksum                                  TRUE
replica-transaction-retries                                  10
replica-type-conversions                                     
replicate-same-server-id                                     FALSE
replication-optimize-for-static-plugin-config                FALSE
replication-sender-observe-commit-only                       FALSE
report-host                                                  (No default value)
report-password                                              (No default value)
report-port                                                  0
report-user                                                  (No default value)
require-secure-transport                                     FALSE
rpl-read-size                                                8192
rpl-stop-replica-timeout                                     31536000
rpl-stop-slave-timeout                                       31536000
safe-user-create                                             FALSE
schema-definition-cache                                      256
secondary-engine-cost-threshold                              100000
secure-file-priv                                             NULL
select-into-buffer-size                                      131072
select-into-disk-sync                                        FALSE
select-into-disk-sync-delay                                  0
server-id                                                    1
server-id-bits                                               32
session-track-gtids                                          OFF
session-track-schema                                         TRUE
session-track-state-change                                   FALSE
session-track-system-variables                               time_zone,autocommit,character_set_client,character_set_results,character_set_connection
session-track-transaction-info                               OFF
sha256-password-auto-generate-rsa-keys                       TRUE
sha256-password-private-key-path                             private_key.pem
sha256-password-proxy-users                                  FALSE
sha256-password-public-key-path                              public_key.pem
shared-memory                                                FALSE
shared-memory-base-name                                      MYSQL
show-create-table-verbosity                                  FALSE
show-gipk-in-create-table-and-information-schema             TRUE
show-old-temporals                                           FALSE
show-replica-auth-info                                       FALSE
show-slave-auth-info                                         FALSE
skip-grant-tables                                            FALSE
skip-name-resolve                                            FALSE
skip-networking                                              FALSE
skip-replica-start                                           FALSE
skip-show-database                                           FALSE
skip-slave-start                                             FALSE
slave-allow-batching                                         TRUE
slave-checkpoint-group                                       512
slave-checkpoint-period                                      300
slave-compressed-protocol                                    FALSE
slave-exec-mode                                              STRICT
slave-load-tmpdir                                            C:\Users\docming\AppData\Local\Temp
slave-max-allowed-packet                                     1073741824
slave-net-timeout                                            60
slave-parallel-type                                          LOGICAL_CLOCK
slave-parallel-workers                                       4
slave-pending-jobs-size-max                                  134217728
slave-preserve-commit-order                                  TRUE
slave-rows-search-algorithms                                 INDEX_SCAN,HASH_SCAN
slave-skip-errors                                            (No default value)
slave-sql-verify-checksum                                    TRUE
slave-transaction-retries                                    10
slave-type-conversions                                       
slow-launch-time                                             2
slow-query-log                                               FALSE
slow-query-log-file                                          D:\Software\mysql-8.0.32-winx64\data\phascolarctos-slow.log
slow-start-timeout                                           15000
socket                                                       MySQL
sort-buffer-size                                             262144
source-verify-checksum                                       FALSE
sporadic-binlog-dump-fail                                    FALSE
sql-generate-invisible-primary-key                           FALSE
sql-mode                                                     ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION
sql-require-primary-key                                      FALSE
ssl                                                          TRUE
ssl-ca                                                       (No default value)
ssl-capath                                                   (No default value)
ssl-cert                                                     (No default value)
ssl-cipher                                                   (No default value)
ssl-crl                                                      (No default value)
ssl-crlpath                                                  (No default value)
ssl-fips-mode                                                OFF
ssl-key                                                      (No default value)
ssl-session-cache-mode                                       TRUE
ssl-session-cache-timeout                                    300
stored-program-cache                                         256
stored-program-definition-cache                              256
super-read-only                                              FALSE
symbolic-links                                               FALSE
sync-binlog                                                  1
sync-master-info                                             10000
sync-relay-log                                               10000
sync-relay-log-info                                          10000
sync-source-info                                             10000
sysdate-is-now                                               FALSE
table-definition-cache                                       2000
table-encryption-privilege-check                             FALSE
table-open-cache                                             4000
table-open-cache-instances                                   16
tablespace-definition-cache                                  256
tc-heuristic-recover                                         OFF
temptable-max-mmap                                           1073741824
temptable-max-ram                                            1073741824
temptable-use-mmap                                           TRUE
terminology-use-previous                                     NONE
thread-cache-size                                            9
thread-handling                                              one-thread-per-connection
thread-stack                                                 1048576
tls-ciphersuites                                             (No default value)
tls-version                                                  TLSv1.2,TLSv1.3
tmp-table-size                                               16777216
tmpdir                                                       C:\Users\docming\AppData\Local\Temp
transaction-alloc-block-size                                 8192
transaction-isolation                                        REPEATABLE-READ
transaction-prealloc-size                                    4096
transaction-read-only                                        FALSE
transaction-write-set-extraction                             XXHASH64
updatable-views-with-limit                                   YES
upgrade                                                      AUTO
validate-config                                              FALSE
validate-user-plugins                                        TRUE
verbose                                                      TRUE
wait-timeout                                                 28800
windowing-use-high-precision                                 TRUE
xa-detach-on-prepare                                         TRUE
```
