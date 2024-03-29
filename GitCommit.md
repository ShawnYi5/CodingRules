## 原则
* 每一次修复作为单独的变更来提交
* 提供有意义的提交信息
* 包含 issue 链接

## 操作
* 每次推送代码前，请仔细检查是否所有需要提交的文件都已经提交
    - 如果发现有漏提交的内容，请使用 `修改上一次提交` 或者 `合并commit` 功能将需要的文件都提交到同一个 commit中

## 文本结构
```
提交类型：Issue编号 简述
更多描述
```

##### 举例
```
fix : AIO/project_main#4899 加大nbd读取超时参数
- 该问题可能触发多个业务过程的超时判断：如 AIO/project_main#4874 等
```

```
bug : AIO/project_main#5495 修正打开备份点时的500错误
- 打开备份点时，如果选择时刻刚好在安全区域内，会发生500错
```

#### 提交类型
* bug
    >> 修正bug类型的issue
* feature
    >> 新增功能类型的issue
* fix
    >> 除开bug与feature类型的issue


#### issue编号
* 如何获取正确的 issue 编号
    - 找到issue页面的url链接，如： `http://172.16.1.11/AIO/project_main/issues/4899`
    - 去掉域名部分，得到 `AIO/project_main/issues/4899`
    - 将最后一个 `issues` 改为 `#`，得到 `AIO/project_main#4899` 即为issue编号


#### 简述
* 控制简述的字数
    - 50个字符以内
    - 详细描述请放到 issue 回复中，或者 放在更多描述字段
* 尽量不要有`逗号` `句号`
    - 如果需要分句才能描述本次修改，那么说明本次提交的内容太多，请分批次提交
* 不要写提交者信息
    - git 日志可以看见是谁提交的，没有人会冒领你的功劳
* 放在第一行，不要换行
    - 换行后，在绝大多数git log浏览器中都是默认折叠第二行以及以后的信息


#### 更多描述
* 使用类似 makedown 的 `-` 符号来进行分组
* 不要填写 `测试建议` ， 请填写到 issue 回复中
* 可以填写关联的更多 issue 编号
* 可以填写为什么做出修改，例如：xxxx用户测试环境，在yyyy情况下触发，关联 zzzz 记录
* 可以填写某些重大修改的更多信息，例如：新增 xxxx 接口，废弃 yyyy 接口
