SIGNMESSAGE


help signmessage
signmessage "address or identity" "message" "currentsig"

Sign a message with the private key of a t-addr or the authorities present in this wallet for an identity

Arguments:
1. "t-addr or identity" (string, required) The transparent address or identity to use for signing.
2. "message"                   (string, required) The message to create a signature of.
2. "cursig"                    (string) The current signature of the message encoded in base 64 if multisig ID

Result:
{
  "hash":"hexhash"         (string) The hash of the message (SHA256, NOT SHA256D)
  "signature":"base64sig"  (string) The aggregate signature of the message encoded in base 64 if all or partial signing successful
}

Examples:

Unlock the wallet for 30 seconds
> verus walletpassphrase "mypassphrase" 30

Create the signature
> verus signmessage "RD6GgnrMpPaTSMn8vai6yiGA7mN4QGPV" "my message"

Verify the signature
> verus verifymessage "RD6GgnrMpPaTSMn8vai6yiGA7mN4QGPV" "signature" "my message"

As json rpc
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "signmessage", "params": ["RD6GgnrMpPaTSMn8vai6yiGA7mN4QGPV", "my message"] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/





signmessage "user22@" "verus is the way"

{
  "hash": "191d3e706f41b9c2104fb97f9676f87387e5e3e2eedf15e3bf6aaafdf6d795df",
  "signature": "AVC/CAADQR9SrpoMKoQdOxCv9OGQ4UL9W6wT/K66BdIV/DvLKgirWC1/aHKh1pGFzf47zLQc9x72OEJI0B/9LCh91/zhRnfsQR/Aip8Iy4qkNyCfwezqc2WWJFnMfO0pAN3has7zVUSQdD8BwPCQdElsxoAfdu4bgceekJuUtkiGoY6hKSpvWYvPQSCQ3S9UDAN8M4SMPvFcOTUW9aj2kkj36OjBsgTTaYv1SFx4FcJhqRD53GpgBNo1gfbIn/h+Cnt+ea6ERFHTzaJp"
}





VERIFYSIGNATURE


help verifysignature

verifysignature '{"address":"i-address or friendly name (t-address checks on simple signature w/hash and prefix, nothing else)",
                  "prefixstring":"extra string that is hashed during signature and must be supplied for verification",
                  "filename":"filepath/filename" |
                    "message":"any message" |
                    "messagehex":"hexdata" |
                    "messagebase64":"base64data" |
                    "datahash":"256bithex",
                  "vdxfkeys":["vdxfkey i-address", ...],
                  "vdxfkeynames":["vdxfkeyname, object for getvdxfid API, or friendly name ID -- no i-addresses", ...],
                  "boundhashes":["hexhash", ...],
                  "hashtype": "sha256" | "sha256D" | "blake2b" | "keccak256"
                  "checklatest": true | false
                  "signature":"verificationsignature"}'


Checks to see if the signature is valid and returns an error for invalid parameters{
  "address":"t-addr or identity"                               (string, required) The transparent address or identity to verify against the signature
  "filename" | "message" | "messagehex" | "messagebase64" | "datahash" (string, required) Data or hash of data signed
  "vdxfkeys":["vdxfkey", ...],                                 (array, optional)  Array of vdxfkeys or ID i-addresses
  "vdxfkeynames":["vdxfkeyname", ...],                         (array, optional)  Array of vdxfkey names or fully qualified friendly IDs
  "boundhashes":["hexhash", ...],                              (array, optional)  Array of bound hash values
  "hashtype"                                                     (string, optional) one of: "sha256", "sha256D", "blake2b", "keccak256", defaults to sha256
  "signature"                                                    (string, optional) The current signature of the message encoded in base 64
  "checklatest"                                                  (bool, optional)   If true, checks signature validity based on latest identity. defaults to false,
                                                                                      which determines validity of signing height stored in signature.
}

Result:
{
  "hash":"hexhash"         (string) The hash of the message (SHA256, NOT SHA256D)
  "signature":"base64sig"  (string) The aggregate signature of the message encoded in base 64 if all or partial signing successful
}

Examples:

Verify the signature
> verus verifysignature '{"identity":"Verus Coin Foundation.vrsc@", "message":"hello world", "signature":"base64sig"}'

As json rpc
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "verifysignature", "params": ['{"identity":"Verus Coin Foundation.vrsc@", "message":"hello world", "signature":"base64sig"}'] }' -H 'content-type: text/plain;' http://127.0.0.1:27486/




EXAMPLES OF SIGNMESSAGE & VERIFYSIGNATURE with RESULTS/OUTPUTS:


./verus signmessage "user22@" "message example 1"

{
  "hash": "5368acaa6a981e854cb179162825484737e1e7dcfdc800d5636784af1b6e5b10",
  "signature": "AWjbCAADQR8sG0duizSlrlkz5/DYf9pvQPfRlDFmP7riVLX0QeKjCWhlbdLQake/Hq/gFyTvQxDcD/d+2H+Fuporln2y8XZrQR/FafMORxrYP+EtInE9XHdGl21dr+FyrIL36cHvwOzGNwPAp986dRaUbMX6EAidZ33qq0L+3IWA8SVDdCMK0GjmQSDavEdPbLpjawjm/QB59nr+Xmcsb/9IVk5+tTja5wATEAnvPOfmJy37OosjHIZih2O5OV7cNANMYJQOmv+R4rIw"
}

./verus verifysignature '{"address":"user22@", "message":"message example 1", "signature":"AWjbCAADQR8sG0duizSlrlkz5/DYf9pvQPfRlDFmP7riVLX0QeKjCWhlbdLQake/Hq/gFyTvQxDcD/d+2H+Fuporln2y8XZrQR/FafMORxrYP+EtInE9XHdGl21dr+FyrIL36cHvwOzGNwPAp986dRaUbMX6EAidZ33qq0L+3IWA8SVDdCMK0GjmQSDavEdPbLpjawjm/QB59nr+Xmcsb/9IVk5+tTja5wATEAnvPOfmJy37OosjHIZih2O5OV7cNANMYJQOmv+R4rIw"}'

{
  "signaturestatus": "verified",
  "system": "VRSCTEST",
  "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "identity": "user22.VRSCTEST@",
  "canonicalname": "user22.vrsctest@",
  "address": "i5uJfUdEB1GN5aZ5XgMfQVVKCaGcwimG2Q",
  "hashtype": "sha256",
  "hash": "5368acaa6a981e854cb179162825484737e1e7dcfdc800d5636784af1b6e5b10",
  "height": 580457,
  "signatureheight": 580456,
  "signature": "AWjbCAADQR8sG0duizSlrlkz5/DYf9pvQPfRlDFmP7riVLX0QeKjCWhlbdLQake/Hq/gFyTvQxDcD/d+2H+Fuporln2y8XZrQR/FafMORxrYP+EtInE9XHdGl21dr+FyrIL36cHvwOzGNwPAp986dRaUbMX6EAidZ33qq0L+3IWA8SVDdCMK0GjmQSDavEdPbLpjawjm/QB59nr+Xmcsb/9IVk5+tTja5wATEAnvPOfmJy37OosjHIZih2O5OV7cNANMYJQOmv+R4rIw"
}





Example: Partially signed using a multisig ID:


./verus signmessage "ai2@" "multisig ftw"

{
  "hash": "4aebf7c418a5d9db6b8194b824db471799496e4ecd441781cb2b302a061e79ca",
  "signature": "AUXbCAABQR8+eouf0m3pWl2GGVF0m05/z92XF0Td6y2Bhj0wUlYT52cVdgc3Pg7J0P83I5rUKmTrDkbyDtG+Z/IvOJdbsj+5"
}


./verus verifysignature '{"address":"ai2@", "message":"multisig ftw", "signature":"AUXbCAABQR8+eouf0m3pWl2GGVF0m05/z92XF0Td6y2Bhj0wUlYT52cVdgc3Pg7J0P83I5rUKmTrDkbyDtG+Z/IvOJdbsj+5"}'

{
  "signaturestatus": "partial",
  "system": "VRSCTEST",
  "systemid": "iJhCezBExJHvtyH3fGhNnt2NhU4Ztkf2yq",
  "identity": "AI2.VRSCTEST@",
  "canonicalname": "ai2.vrsctest@",
  "address": "iQjrxAJrdWbmkAhVfWMA9zEXPen5BrU9AN",
  "hashtype": "sha256",
  "hash": "4aebf7c418a5d9db6b8194b824db471799496e4ecd441781cb2b302a061e79ca",
  "height": 580444,
  "signatureheight": 580421,
  "signature": "AUXbCAABQR8+eouf0m3pWl2GGVF0m05/z92XF0Td6y2Bhj0wUlYT52cVdgc3Pg7J0P83I5rUKmTrDkbyDtG+Z/IvOJdbsj+5"
}







