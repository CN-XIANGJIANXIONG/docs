
电子存证合约
============

代码样例参看：contractsdk/go/example/eleccert.go

电子存证合约简介
----------------

电子存证应用主要是通过区块链解决的存证中的信任问题，而存证合约只需做简单的读写操作即可

电子存证合约具备的读写操作
--------------------------

- 通过invoke方法，put存证到区块链
- 通过query方法，get存证

调用json文件示例
----------------

Invoke

./xchain-cli native invoke -a '下面json中args字段的内容' --method save -H localhost:37101 eleccert

.. code-block:: console
    :linenos:

    {
        "module_name": "native",       // native or wasm
        "contract_name": "eleccert",   // contract name
        "method_name": "invoke",       // invoke or query
        "args": {
            "owner": "aaa",            // user name
            "filehash": "存证文件的hash值",
            "timestamp": "存证的timestamp"
        }
    }

Query

./xchain-cli native query -a 'args内容' --method query -H localhost:37101 eleccert

.. code-block:: console
    :linenos:

    {
        "module_name": "native",       // native or wasm
        "contract_name": "eleccert",   // contract name
        "method_name": "query",        // invoke or query
        "args": {
            "owner": "aaa",            // user name
            "filehash": "文件hash值"
        }
    }
    // output
    {
        "filehash": "文件hash值",
        "timestamp": "文件存入timestamp"
    }