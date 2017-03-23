```toml
title = "RabbitMQ常用命令"
slug = "RabbitMQ常用命令"
desc = "RabbitMQ常用命令"
date = "2016-12-09 18:57:16"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["RabbitMQ"]
```

###备注：所有命令以`rabbitmqctl`开始
    stop [<pid_file>]
    stop_app
    start_app
    wait <pid_file>
    reset
    force_reset
    rotate_logs <suffix>
    hipe_compile <directory>
    
    join_cluster <clusternode> [--ram]
    cluster_status
    change_cluster_node_type disc | ram
    forget_cluster_node [--offline]
    rename_cluster_node oldnode1 newnode1 [oldnode2] [newnode2 ...]
    update_cluster_nodes clusternode
    force_boot
    sync_queue [-p <vhost>] queue
    cancel_sync_queue [-p <vhost>] queue
    purge_queue [-p <vhost>] queue
    set_cluster_name name
    
    add_user <username> <password> #新增用户
    delete_user <username> #删除用户
    change_password <username> <newpassword> #修改密码
    clear_password <username> #清空密码
    authenticate_user <username> <password>
    set_user_tags <username> <tag> ...  #设置用户角色，Tag可选administrator，monitoring，policymaker，management，或其他自定义名称
    list_users #查看用户列表
    
    add_vhost <vhost>
    delete_vhost <vhost>
    list_vhosts [<vhostinfoitem> ...]
    set_permissions [-p <vhost>] <user> <conf> <write> <read> #设置用户权限 例如：rabbitmqctl set_permissions -p vhost username ".*" ".*" ".*"
    clear_permissions [-p <vhost>] <username>
    list_permissions [-p <vhost>]  #查看指定vhost所有用户的权限
    list_user_permissions <username>
    
    set_parameter [-p <vhost>] <component_name> <name> <value>
    clear_parameter [-p <vhost>] <component_name> <key>
    list_parameters [-p <vhost>]
    
    set_policy [-p <vhost>] [--priority <priority>] [--apply-to <apply-to>]
    <name> <pattern>  <definition>
    clear_policy [-p <vhost>] <name>
    list_policies [-p <vhost>]
    
    list_queues [-p <vhost>] [--offline|--online|--local] [<queueinfoitem> ...]
    list_exchanges [-p <vhost>] [<exchangeinfoitem> ...]
    list_bindings [-p <vhost>] [<bindinginfoitem> ...]
    list_connections [<connectioninfoitem> ...]
    list_channels [<channelinfoitem> ...]
    list_consumers [-p <vhost>]
    status
    node_health_check
    environment
    report
    eval <expr>
    
    close_connection <connectionpid> <explanation>
    trace_on [-p <vhost>]
    trace_off [-p <vhost>]
    set_vm_memory_high_watermark <fraction>
    set_vm_memory_high_watermark absolute <memory_limit>
    set_disk_free_limit <disk_limit>
    set_disk_free_limit mem_relative <fraction>
    encode [--decode] [<value>] [<passphrase>] [--list-ciphers] [--list-hashes]
    [--cipher <cipher>] [--hash <hash>] [--iterations <iterations>]
    
    
    
### 启用管理页面
    rabbitmq-plugins enable rabbitmq_management


