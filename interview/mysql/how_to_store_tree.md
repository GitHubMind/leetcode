# How to store tree


# parent Id tree
```sql

CREATE TABLE `menu` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(50) NOT NULL,
  `parent_id` int(11) NOT NULL DEFAULT '0',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB;
```

优化
# optimize  (add path column)


```sql

    CREATE TABLE `menu_path` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(50) NOT NULL,
  `parent_id` int(11) NOT NULL DEFAULT '0',
  `path` varchar(255) NOT NULL DEFAULT '',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB;
```


# optimize (add order column)

这个使用先序树的顺序来做,应该去做一下leetcode在用到业务里面


# OKR软件使用手册

## 目录

1. **简介**
   - 1.1 软件概述
   - 1.2 主要功能和目的

2. **开始使用**
   - 2.1 访问对应组织的网站
     - 2.1.1 南田
     - 2.1.2 数思(原云顶)
     - 2.1.3 驰鲸(原商谷)
     - 2.1.4 乐科云(原乐科)
     - 2.1.5 悠聊(原尚迅)

3. **角色和权限**
   - 3.1 总负责人和负责人的区别

4. **创建OKR**
   - 4.1 登录和界面导览
   - 4.2 创建新的Objective
   - 4.3 添加关键结果（Key Results）
   - 4.4 保存和提交

5. **更新OKR**
   - 5.1 跟踪和更新OKR
   - 5.2 输入最新进展
   - 5.3 保存更新

6. **顺延机制**
   - 6.1 顺延OKR的步骤
   - 6.2 注意事项

7. **Objective修改限制**

8. **上级负责人接收修改信息**

9. **上级管理下级的OKR**
   - 9.1 指派Objective
   - 9.2 指派范围
   - 9.3 重要注意事项

10. **删除Objective及其所有子集的规则**

11. **对员工评分**
    - 11.1 设置Objective和Key Results的权重
    - 11.2 进行评分
    - 11.3 添加评论和反馈

12. **OKR汇总和导出**
    - 12.1 计算公式
    - 12.2 Excel导出功能

13. **联系和支持**
    - 13.1 联系方式
