## Postorius Settings
本文主要介绍在Postorius界面上关于邮件列表的各项设置

### List Identity
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | Show list on index page | 选择是否将此列表包括在所有列表的列表中 | 公开列表选是，私有列表选否 |
 | Description | 当邮件列表与其他邮件列表一起列出时，或在邮件头中列出时，使用此描述。它应该尽可能简洁，同时还要确定列表是什么 |空 |
 | Information | 此邮件列表的详细描述 | 空 |
 | Display name | web界面中显示的名称 | 默认与邮件列表同名，首字母大写 |
 | Subject prefix | 转发邮件时主题的前缀 | 默认为[Display name] |
 
### Automatic Responses
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | Autorespond to list owner | 自动响应列表所有者 | No automatic response |
 | Autoresponse owner text | 自动响应所有者文本 | 空 |
 | Autorespond postings | 自动响应邮件 | No automatic response |
 | Autoresponse postings text | 自动响应邮件文本 | 空 |
 | Autorespond requests | 自动响应请求 | No automatic response |
 | Autoresponse request text | 自动响应请求文本 | 空 |
 | Autoresponse grace period | 自动响应宽限期 | 90d |
 | Notify users of held messages| 通知用户邮件被保留 | 是 |
 | Send welcome message | 向订阅成功的成员发送欢迎信息 | 是 |
 | URI for the welcome message | 欢迎信息的URI | 空 |
 | URI for the good bye message | 再见信息的URI | 空 |
 | Admin immed notify | 即时通知管理 | 是 |
 | Notify admin of membership changes | 成员身份变更通知 | 是 |

### Alter Messages
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | Filter content | Mailman是否应该根据以下设置过滤列表流量的内容 | 否 |
 | Collapse alternatives | Mailman是否应折叠第一部分内容的多部分/备选方案 | 是 |
 | Convert html to plaintext | Mailman是否应该将文本/html部分转换为纯文本？此转换发生在MIME附件被剥离之后 | 否 |
 | Anonymous list | 隐藏邮件的发件人，将其替换为列表地址（删除发件人、发件人和答复字段） | 否 |
 | Include RFC2369 headers |RFC 2369定义了一组通常添加到发送到列表成员身份的每条消息中的List-*头，这些功能极大地帮助了使用符合标准的邮件阅读器的最终用户| 是 |
 | Include the list post header | 包括列表邮件标题 | 是 |
 | Explicit reply-to address | 此选项允许管理员设置显式回复地址，仅当回复到设置为使用显式设置的标头时使用它 | 空 |
 | First strip reply to | 是否删除所有原始邮件中的Reply-To | 否 |
 | Reply goes to list | 回复转向列表 | No Munging |
 | Pipeline | 邮件列表的pipeline类型 | default-posting-pipeline |

### DMARC Mitigations
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | DMARC mitigation action | DMARC缓解措施 | No DMARC mitigations |
 | DMARC Mitigate unconditionally | DMARC无条件缓解 | 是 |
 | DMARC rejection notice | DMARC拒绝通知 | 空 |
 | DMARC wrapped message text | 当wrap message的DMARC缓解操作应用时，要作为单独的文本/纯MIME部分添加到wrap message中原始消息部分之前的文本 | 空 |

### Digest
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | Digest size threshold | 摘要大小阈值(kb) | 30.0 |

### Message Acceptance
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | Acceptable aliases | 每行一个地址和正则匹配的地址，当启用“require_explicit_destination”时，可以在To:或Cc:中代替列表发布地址 | 空 |
 | Require Explicit Destination | 确保列表投递地址或可接受的别名明确显示在投递的收件人或抄送中 | 是 |
 | Administrivia | Administrivia测试将检查帖子，看看它是否真的是管理请求（如订阅、取消订阅等），并将其添加到管理请求队列中，在此过程中通知管理员新的请求 | 是 |
 | Default action to take when a member posts to the list | 成员发布到列表时要执行的默认操作 | Accept immediately (bypass other rules) |
 | Default action to take when a non-member posts to the list | 非成员发布到列表时要执行的默认操作 | Hold for moderation |
 | Maximum message size | 允许的最大邮件大小(kb)，主要用来限制邮件附件大小 | 40000 |
 | Maximum number of recipients | 邮件的最大收件人数，用来防止大量邮件被接受，值为0将禁用检查 | 500 |

### Archiving
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | Archive policy | 归档策略 | 公开列表选Public archives， 私有列表选Private archives |
 | Active archivers | 在用的归档器 | hyperkitty |

### Subscription Policy
 | 选项 | 描述 | 默认值 |
 | :---: | :---: | :---  |
 | Subscription Policy | 订阅策略 | 确认（需订阅者通过邮件确认订阅） |
 
 ---
 本文中多数选项的描述并未按web界面的描述完全翻译，如有疑问，可结合web界面描述进行理解或与作者沟通交流
