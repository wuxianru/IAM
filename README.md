# IAM
Internet Application Mock Server

## 需求背景

	目前测试环节主要存在问题：

- 测试数据依赖后台服务、若数据不能满足测试需求，沟通成本高。
- 缺乏有效的自动化回归测试手段
- 单元测试不充分、过于依赖集成测试及业务验收测试。

## 需求的业务可行性和必要性

	    测试环节是保证项目质量的最重要环节，提供方便有效的挡板服务队提升开发质量提高测试、开发效率有重要的帮助。同时数据挡板也是自动化回归测试的重要支持手段。

## 需求目标

挡板能够有效支撑单元测试及集成测试；

支持自动化工具调度，Junit等；

支持测试人员手工发起测试；

能够基于案例管理挡板返回数据；

方便开发、测试人员维护及使用；

支持目前常用的报文包括但不限于，sop、soap、tcp定长、xml、json，方便集成第三方报文解析组建；



## 需求范围

该需求属于互联网应用系统群开发测试平台优化，适用于我行互联网应用系统群所有项目。本需求仅包含挡板部分，后期与案例库结合内容，后续另行讨论。



## 功能性需求

基于挡板功能测试的过程归纳如下：



### 前期准备：

- 开发测试人员通过挡板管理界面维护挡板数据，并为数据设置案例编号。
- 挡板服务将测试数据及相关信息存入挡板数据库。



### 测试过程：

- 设置挡板案例（自动化测试时通过api设置、测试人员手工测试时通过界面设置）
- 调用被测试程序（自动化测试调起或测试人员手工发起）
- 应用程序发送请求至挡板
- 挡板服务根据预设案例编号、交易名称获取测试数据
- 挡板将测试案例数据返回至待测应用程序
- 待测应用程序将数据返回（自动化测试场景下由程序验证返回，人工测试场景下由测试人员验证返回数据）。
- 从挡板获取代测程序并验证测试程序请求数据正确性。

### 基于以上过程，测试挡板因提供以下功能

| 管理界面 |              |
| -------- | ------------ |
|          | 挡板数据新增 |
|          | 挡板数据查询 |
|          | 挡板数据修改 |
|          | 挡板数据删除 |
|          | 案例数据新增 |
|          | 案例数据查询 |
|          | 案例数据修改 |
|          | 案例数据删除 |
|          | 设置数据标签 |
|          | 设置案例标签 |
|          | 数据导入导出 |
|          | 当前案例设置 |
|          | 请求数据查询 |
| 接口类   |              |
|          | 挡板交易接口 |
|          | 当前案例设置 |
|          | 请求数据查询 |



## 非功能性需求

- 容器化部署

考虑到互联网条线开发测试规模巨大、需要能够灵活部署多套挡板环境，因此挡板需要支持容器化部署

- 性能要求，性能开销较小，以较少的资源能满足各项功能测试性能要求。
