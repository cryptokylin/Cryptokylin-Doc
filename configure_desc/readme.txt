# the endpoint upon which to listen for incoming connections (eosio::bnet_plugin)
# 在启用 eosio:bnet_plugin 时，用于指定bnet(基于Websocket)监听的端口
bnet-endpoint = 0.0.0.0:4321

# the number of threads to use to process network messages (eosio::bnet_plugin)
# 在启用 eosio:bnet_plugin 时，用于指定开启多少线程(ThreadPool + boost::asio
)处理网络信息，最大值为 8，会生成一个该大小的ThreadPool来处理数据的同步
# bnet-threads =

# remote endpoint of other node to connect to; Use multiple bnet-connect options as needed to compose a network (eosio::bnet_plugin)
# 在启用 eosio:bnet_plugin 时，用于指定启用bnet方式的目标服务器和端口
# bnet-connect =

# this peer will request no pending transactions from other nodes (eosio::bnet_plugin)
# 在启用 eosio:bnet_plugin 时，用于指定是否同步未被处理的交易
# block 状态参考 incomplete -> complete -> validated -> irreversible
# libraries/chain/include/eosio/chain/controller.hpp
bnet-no-trx = false

# the location of the blocks directory (absolute path or relative to application data dir) (eosio::chain_plugin)
# 指定存储区块文件的目录
blocks-dir = "blocks"

# Pairs of [BLOCK_NUM,BLOCK_ID] that should be enforced as checkpoints. (eosio::chain_plugin)
# 指定需要进行检查的区块信息，格式为 [BLOCK_NUM1,BLOCK_ID1],[BLOCK_NUM2,BLOCK_ID2]
# checkpoint =

# Override default WASM runtime (eosio::chain_plugin)
# 指定默认的运行时库，可选项有 wavm, binaryen; 如果需要replay可以设置成 wavm 可以提高速度，同步正常高度后再改成binaryen(默认)即可
# wasm-runtime =

# Maximum size (in MB) of the chain state database (eosio::chain_plugin)
# 指定 state/shared_memory.bin 链状态数据文件的大小，建议大于>8GB
chain-state-db-size-mb = 8192

# Maximum size (in MB) of the reversible blocks database (eosio::chain_plugin)
# 指定 blocks/reversible/shared_memory.bin 待确定块数据文件的大小
reversible-blocks-db-size-mb = 340

# print contract's output to console (eosio::chain_plugin)
# 指定是否将合约执行结果打印到nodeos进程对应的stdout
contracts-console = false

# Account added to actor whitelist (may specify multiple times) (eosio::chain_plugin)
# 指定账户白名单
# actor-whitelist =

# Account added to actor blacklist (may specify multiple times) (eosio::chain_plugin)
# 指定账户黑名单
# actor-blacklist =

# Contract account added to contract whitelist (may specify multiple times) (eosio::chain_plugin)
# 指定合约白名单
# contract-whitelist =

# Contract account added to contract blacklist (may specify multiple times) (eosio::chain_plugin)
# 指定合约黑名单
# contract-blacklist =

# Track actions which match receiver:action:actor. Actor may be blank to include all. Receiver and Action may not be blank. (eosio::history_plugin)
# 指定需要记录的那些账户、合约Action的调用记录，请避免使用*，捕获所有记录会导致配置的内存用尽；
# filter-on =

# PEM encoded trusted root certificate (or path to file containing one) used to validate any TLS connections made.  (may specify multiple times)
#  (eosio::http_client_plugin)
# https-client-root-cert =

# true: validate that the peer certificates are valid and trusted, false: ignore cert errors (eosio::http_client_plugin)
https-client-validate-peers = 1

# The local IP and port to listen for incoming http connections; set blank to disable. (eosio::http_plugin)
http-server-address = 0.0.0.0:8888

# The local IP and port to listen for incoming https connections; leave blank to disable. (eosio::http_plugin)
# 支持HTTPS的设置请参考：https://steemit.com/eos/@eosrio/using-ssl-with-eos-io-nodes
# https-server-address =

# Filename with the certificate chain to present on https connections. PEM format. Required for https. (eosio::http_plugin)
# https-certificate-chain-file =

# Filename with https private key in PEM format. Required for https (eosio::http_plugin)
# https-private-key-file =

# Specify the Access-Control-Allow-Origin to be returned on each request. (eosio::http_plugin)
# access-control-allow-origin =

# Specify the Access-Control-Allow-Headers to be returned on each request. (eosio::http_plugin)
# access-control-allow-headers =

# Specify the Access-Control-Max-Age to be returned on each request. (eosio::http_plugin)
# access-control-max-age =

# Specify if Access-Control-Allow-Credentials: true should be returned on each request. (eosio::http_plugin)
access-control-allow-credentials = false

# The actual host:port used to listen for incoming p2p connections. (eosio::net_plugin)
p2p-listen-endpoint = 0.0.0.0:9876

# An externally accessible host:port for identifying this node. Defaults to p2p-listen-endpoint. (eosio::net_plugin)
# p2p-server-address =

# The public endpoint of a peer node to connect to. Use multiple p2p-peer-address options as needed to compose a network. (eosio::net_plugin)
# p2p-peer-address =

# Maximum number of client nodes from any single IP address (eosio::net_plugin)
# 此处请注意，如果nodeos是部署在LoadBalance或高防IP之后请将该值设置一个更大的值，因为此种情况对于nodeos来源IP都是Load Balance 或 高防IP
p2p-max-nodes-per-host = 1

# The name supplied to identify this node amongst the peers. (eosio::net_plugin)
agent-name = "EOS Test Agent"

# Can be 'any' or 'producers' or 'specified' or 'none'. If 'specified', peer-key must be specified at least once. If only 'producers', peer-key is not required. 'producers' and 'specified' may be combined. (eosio::net_plugin)
allowed-connection = any

# Optional public key of peer allowed to connect.  May be used multiple times. (eosio::net_plugin)
# peer-key =

# Tuple of [PublicKey, WIF private key] (may specify multiple times) (eosio::net_plugin)
# peer-private-key =

# Maximum number of clients from which connections are accepted, use 0 for no limit (eosio::net_plugin)
# 此处请注意，如果nodeos是部署在LoadBalance或高防IP之后请将该值设置一个更大的值，因为此种情况对于nodeos来源IP都是Load Balance 或 高防IP
max-clients = 25

# number of seconds to wait before cleaning up dead connections (eosio::net_plugin)
connection-cleanup-period = 30

# True to require exact match of peer network version. (eosio::net_plugin)
network-version-match = 0

# number of blocks to retrieve in a chunk from any individual peer during synchronization (eosio::net_plugin)
sync-fetch-span = 100

# maximum sizes of transaction or block messages that are sent without first sending a notice (eosio::net_plugin)
# 指接收到多少字节的数据就开始给其他节点进行广播
max-implicit-request = 1500

# Enable block production, even if the chain is stale. (eosio::producer_plugin)
# 指定是否在本地区块与链上其他节点差距过大时仍可以出块，一般用于测试网络
enable-stale-production = false

# Start this node in a state where production is paused (eosio::producer_plugin)
pause-on-startup = false

# Limits the maximum time (in milliseconds) that is allowed a pushed transaction's code to execute before being considered invalid (eosio::producer_plugin)
# EOS主网初期建议将该值调大一些，比如 300
max-transaction-time = 30

# Limits the maximum age (in seconds) of the DPOS Irreversible Block for a chain this node will produce blocks on (use negative value to indicate unlimited) (eosio::producer_plugin)
# 指定距离上次LIB区块时间差多少之内可以继续出块，大于该时间就不会出块，-1 默认为无限制
max-irreversible-block-age = -1

# ID of producer controlled by this node (e.g. inita; may specify multiple times) (eosio::producer_plugin)
# producer-name =
producer-name = eosio

# (DEPRECATED - Use signature-provider instead) Tuple of [public key, WIF private key] (may specify multiple times) (eosio::producer_plugin)
# private-key =

# Key=Value pairs in the form <public-key>=<provider-spec>
# Where:
#    <public-key>       is a string form of a vaild EOSIO public key
#
#    <provider-spec>    is a string in the form <provider-type>:<data>
#
#    <provider-type>    is KEY, or KEOSD
#
#    KEY:<data>         is a string form of a valid EOSIO private key which maps to the provided public key
#
#    KEOSD:<data>       is the URL where keosd is available and the approptiate wallet(s) are unlocked (eosio::producer_plugin)
signature-provider = EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV=KEY:5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3

# Limits the maximum time (in milliseconds) that is allowd for sending blocks to a keosd provider for signing (eosio::producer_plugin)
keosd-provider-timeout = 5

# Lag in number of blocks from the head block when selecting the reference block for transactions (-1 means Last Irreversible Block) (eosio::txn_test_gen_plugin)
# 设置生成交易记录中 ref_block_num 使用头部区块之前的第几个区块，0 使用最新头部区块，-1 使用LIB区块
txn-reference-block-lag = 0

# The path of the wallet files (absolute path or relative to application data dir) (eosio::wallet_plugin)
wallet-dir = "."

# Timeout for unlocked wallet in seconds (default 900 (15 minutes)). Wallets will automatically lock after specified number of seconds of inactivity. Activity is defined as any wallet command e.g. list-wallets. (eosio::wallet_plugin)
unlock-timeout = 900

# eosio key that will be imported automatically when a wallet is created. (eosio::wallet_plugin)
# eosio-key =

# Plugin(s) to enable, may be specified multiple times
# plugin =
plugin = eosio::chain_api_plugin
plugin = eosio::history_api_plugin


