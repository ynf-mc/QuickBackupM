# QuickBackupM

一个支持多槽位的快速备份＆回档插件

兼容 [MCDaemon](https://github.com/kafuuchino-desu/MCDaemon) 以及 [MCDReforged](https://github.com/Fallen-Breath/MCDReforged)

备份的存档将会存放至 qb_multi 文件夹中，文件目录格式如下：
```
mcd_root/
    server.py
    
    server/
        world/
        
    qb_multi/
        slot1/
            info.json
            world/
            
        slot2/
            ...
        ...
        
        overwrite/
            info.txt
            world/
```

## 命令格式说明

`!!qb` 显示帮助信息

`!!qb make [<comment>]` 创建一个储存至槽位 `1` 的备份，并将后移已有槽位。`<comment>` 为可选存档注释

`!!qb back [<slot>]` 回档为槽位 `<slot>` 的存档。当 `<slot>` 参数被指定时将会回档为槽位 `<slot>`

`!!qb confirm` 在执行 `back` 后使用，再次确认是否进行回档

`!!qb abort` 在任何时候键入此指令可中断回档

`!!qb share` 分享存档至指定目录。在 TIS 服务器中使用，其他环境下忽略即可

`!!qb list` 显示各槽位的存档信息

当 `<slot>` 未被指定时默认选择槽位 `1`

在 MCDR 环境下，默认配置下 `!!qb back` 以及 `!!qb share` 需要权限等级 `helper`

## 一些常量说明

调整这些常量的数值也就是在配置 QuickBackupM 插件

### SlotCount

默认值: `SlotCount = 5`

存档槽位的数量

### Prefix

默认值: `Prefix = '!!qb'`

触发指令的前缀

### BackupPath

默认值: `BackupPath = './qb_multi'`

备份储存的路径

### WorldNames

默认值:

```
WorldNames = [
    'world',
]
```

需要备份的世界文件夹列表，原版服务端只会有一个世界，在默认值基础上填上世界文件夹的名字即可

对于非原版服务端如水桶、水龙头服务端，会有三个世界文件夹，此时可填写：
```
WorldNames = [
    'world',
    'world_nether',
    'world_the_end',
]
```

### MinimumPermissionLevel

默认值: `MinimumPermissionLevel = 2`

一个整数，代表使用 `!!qb back` 以及 `!!qb share` 需要权限等级。数值含义见[此处](https://github.com/Fallen-Breath/MCDReforged/blob/master/doc/readme_cn.md#权限)
