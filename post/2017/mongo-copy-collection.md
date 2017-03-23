```toml
title = "MongoDB拷贝命令实现复制collection"
slug = "mongo-copy-collection.md"
desc = "MongoDB拷贝命令实现复制collection"
date = "2017-03-09 18:48:26"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["MongoDB"]
```

    db.collection(源表).find().forEach(
        function(x){
            db.collection_bak.insert(x);
        });
