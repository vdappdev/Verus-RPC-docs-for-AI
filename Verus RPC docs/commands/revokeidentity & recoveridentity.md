REVOKEIDENTITY

help revokeidentity
revokeidentity "nameorID" (returntx) (tokenrevoke) (feeoffer) (sourceoffunds)



Arguments
       "returntx"                        (bool,   optional) defaults to false and transaction is sent, if true, transaction is signed by this wallet and returned
       "tokenrevoke"                     (bool,   optional) defaults to false, if true, the tokenized ID control token, if one exists, will be used to revoke
       "feeoffer"                        (value,  optional) non-standard fee amount to pay for the transaction
       "sourceoffunds"                   (string, optional) transparent or private address to source all funds for fees to preserve privacy of the identity

Result:

Examples:
> verus revokeidentity "nameorID"
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "revokeidentity", "params": ["nameorID"] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



Example & Result/Output:

./verus revokeidentity "ai2@" "" "" "0.0001" "dev28@"

6c558cbcc922ef8e350717bbcd3ad9b30458371dfd6bb66c9543ddc7f6096926




RECOVERIDENTITY

help recoveridentity
recoveridentity "jsonidentity" (returntx) (tokenrecover) (feeoffer) (sourceoffunds)



Arguments
       "returntx"                        (bool,   optional) defaults to false and transaction is sent, if true, transaction is signed by this wallet and returned
       "tokenrecover"                    (bool,   optional) defaults to false, if true, the tokenized ID control token, if one exists, will be used to recover
       "feeoffer"                        (value,  optional) non-standard fee amount to pay for the transaction
       "sourceoffunds"                   (string, optional) transparent or private address to source all funds for fees to preserve privacy of the identity

Result:

Examples:
> verus recoveridentity '{"name" : "myname"}'
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "recoveridentity", "params": ['{"name" : "myname"}'] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/



Example & Result/Output:

run recoveridentity '{"name":"AI2@", "primaryaddresses":["RGi75h173LD84tTThCu73B9Dp6rupM5zoz"], "minimumsignatures":1}' "" "" "0.0001" "dev28@"

e394ec980bbd8adf62864f3842277f541c500179c6d8d9d0a9203b9eb219478d


