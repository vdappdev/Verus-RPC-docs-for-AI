UPDATEIDENTITY


updateidentity "jsonidentity" (returntx) (tokenupdate) (feeoffer) (sourceoffunds)



Arguments
       "jsonidentity"                    (obj,    required) new definition of the identity
       "returntx"                        (bool,   optional) defaults to false and transaction is sent, if true, transaction is signed by this wallet and returned
       "tokenupdate"                     (bool,   optional) defaults to false, if true, the tokenized ID control token, if one exists, will be used to update
                                                              which enables changing the revocation or recovery IDs, even if the wallet holding the token does not
                                                              control either.
       "feeoffer"                        (value,  optional) non-standard fee amount to pay for the transaction
       "sourceoffunds"                   (string, optional) transparent or private address to source all funds for fees to preserve privacy of the identity

Result:
   hex string of either the txid if returnhex is false or the hex serialized transaction if returntx is true

Examples:
> verus updateidentity '{"name" : "myname"}'
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "updateidentity", "params": ['{"name" : "myname"}'] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/


"RGi75h173LD84tTThCu73B9Dp6rupM5zoz", "RE7Rt2ndJyeuVcCDjJikHwv6x6krB5KqTN", "RMJaWvqoyyd44yAMuzHcPHCbXZy4KT2YUN"

updateidentity '{"name":"user22@", "primaryaddresses":["RGi75h173LD84tTThCu73B9Dp6rupM5zoz", "RE7Rt2ndJyeuVcCDjJikHwv6x6krB5KqTN", "RMJaWvqoyyd44yAMuzHcPHCbXZy4KT2YUN"], "minimumsignatures":2}' "" "" "0.0001" "dev28@"

db18d68823a9aebb9b8862ae50eb3b6cc686f6cc7cd83099daf8e59ef58a7419



updateidentity '{"name":"pear", "parent":"kaiju", "primaryaddresses":["RGi75h173LD84tTThCu73B9Dp6rupM5zoz", "RE7Rt2ndJyeuVcCDjJikHwv6x6krB5KqTN", "RMJaWvqoyyd44yAMuzHcPHCbXZy4KT2YUN"], "minimumsignatures":2}' "" "" "0.0001" "zs1fquzxeqxuzxjh54w9mkz7p3ttf6veeen99rd8mwmrg5f29h2mfz96yn9dvetdfj5yrng6qemyyg"

274f8474716fc2a595f504add9c3df5fcfcda954798ce78b12e43e223241a0c7



updateidentity '{"name":"AI2@", "primaryaddresses":["RGi75h173LD84tTThCu73B9Dp6rupM5zoz", "RPSGdnEa5dU61hE7CbhN8D9PSR7q3ZSgUs"], "minimumsignatures":2}' "" "" "0.0001" "dev28@"

c31c0b50e6b2adb032008abc12d983e40de183bb85116f355855a99e62551cb9

