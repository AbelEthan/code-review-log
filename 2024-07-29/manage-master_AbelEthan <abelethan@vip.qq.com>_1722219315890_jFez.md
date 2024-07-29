根据提供的Git diff记录，以下是对代码变更的评审：

### DiskBaseinfoApi.java
- **变更**：`parenId` 错误地拼写为 `parentId`。
- **评审**：这是一个拼写错误，应当及时修正以避免未来的混淆和错误。拼写错误可能是由疏忽造成的，建议在代码审查过程中仔细检查变量和方法的命名。

### DiskNoticeApi.java
- **变更**：添加了一个新的方法 `getChildren` 来根据文件夹id获取共享的文件列表。
- **评审**：这是一个合理的扩展，如果业务逻辑中确实需要根据文件夹id来获取文件列表，这个方法是有用的。确保这个新方法在单元测试中得到了适当的测试。

### DiskBaseinfoService.java
- **变更**：添加了一个新方法 `findListByParentId` 来根据网盘父级id查询网盘信息列表。
- **评审**：这是一个功能性的扩展，如果业务逻辑中确实需要根据父级id来获取子文件夹信息，这个方法是合理的。确保这个新方法在单元测试中得到了适当的测试。

### DiskNoticeService.java
- **变更**：添加了一个新方法 `findDiskChildrenFileList` 来查找共享文件夹子集列表。
- **评审**：这个方法与 `DiskBaseinfoService` 中的 `findListByParentId` 方法相对应，确保这两个服务层方法之间的接口是一致的。如果这个方法是为了在服务层调用，确保它在单元测试中得到了适当的测试。

### DiskBaseinfoMapper.java
- **变更**：添加了一个新方法 `selectListByParentId` 来查询子集网盘信息列表。
- **评审**：这个Mapper层的变更与 `DiskBaseinfoService` 中的方法相对应，确保SQL查询能够正确执行。确保这个新方法在单元测试中得到了适当的测试。

### DiskBaseinfoMapper.xml
- **变更**：添加了一个新的SQL查询 `selectListByParentId`。
- **评审**：确保这个SQL查询能够正确执行并且返回预期的结果。如果数据库结构有变化，需要确保这个查询不会引入错误。

### DiskBaseinfoServiceImpl.java
- **变更**：添加了一个新方法 `findListByParentId` 来实现 `DiskBaseinfoService` 的接口。
- **评审**：确保这个方法在实现逻辑上与 `DiskBaseinfoService` 中的声明一致，并且单元测试验证了其正确性。

### DiskNoticeServiceImpl.java
- **变更**：添加了一个新方法 `findDiskChildrenFileList` 来实现 `DiskNoticeService` 的接口。
- **评审**：确保这个方法在实现逻辑上与 `DiskNoticeService` 中的声明一致，并且单元测试验证了其正确性。

### DiskNoticeController.java
- **变更**：添加了一个新方法 `getChildren` 来处理基于文件夹id的文件列表请求。
- **评审**：确保这个方法与前端逻辑一致，并且能够处理请求并返回正确的响应。

### OaNoticeUser.java
- **变更**：移除了 `@TableId` 和 `@TableName` 注解。
- **评审**：如果这些注解不再需要，那么移除它们是合理的。但是，如果这些注解是为了与数据库表映射，那么需要确保这种映射方式仍然有效。

总的来说，这些变更似乎是业务逻辑的正常扩展。然而，重要的是要确保所有新的功能都得到了适当的测试，并且代码变更没有引入新的bug。此外，拼写错误应该得到修正。