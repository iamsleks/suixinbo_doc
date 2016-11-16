### 快速参数配置
在启动开发前，我们需要进行一些应用、账号、编解码参数的配置。这些配置都可以在腾讯云的控制台完成。
### 第一步 创建应用
1. 考虑到一个公司可能会开发多个应用，所以一个腾讯视频云的账号可以创建多个互动直播应用。但不同应用之间的数据是相互隔离的，不能互相访问。如果有多个应用之间需要相互访问，我们建议使用同一个appid，
2. 进入腾讯云控制台，找到互动直播业务，然后在应用列表点击“创建应用接入”按钮，填写应用名称，点“确定”按钮就创建了一个应用。
3. 应用创建完成后，在应用列表里可以看到 <b>`SDKAPPID`</b> ，后台会用这个参数来识别应用的身份。
4. 如果多个应用之间需要相互访问，我们建议使用同一个<b>`SDKAPPID`</b>，开发者来确保不同应用之间的账号分配不会重复。

### 第二步 选择账号认证方式

1. 为了在互动直播应用中标示用户的身份，我们需要选择一个和腾讯视频云之间进行账号身份认证的方式。
2. 账号身份认证的方式分<b>`独立模式`</b>和<b>`托管模式`</b>两种。<br/>
独立模式是指，用户注册和身份验证由开发者负责，开发者和腾讯之间通过签名验证建立信任关系。绝大部分用户都选择这种模式。<br/>
托管模式是指腾讯云为开发者提供APP帐号的密码注册、存储和密码验证。适用于快速体验功能的场景。<br/>
3. 在应用列表中选择我们刚才新建的应用，点击“应用配置”链接。然后在基础配置中找到“账号集成体系”。填写账号名称，选择独立模式或托管模式，确定后可以在页面上看到 <b>`accountType`</b> 。这个参数的值在开发中也会用到。

### 第三步 配置场景和角色
在应用列表中选择我们刚才新建的应用，点击“应用配置”链接。然后选择“SPEAR引擎配置”tab。    

1. 选择应用场景<br/>
当前默认的场景是实时通信。互动直播业务点”变更场景“链接，选择互动直播场景。
2. 角色的意义<br/>
角色的意义是用来标示一套音视频编码参数。sdk会按照给的角色名字，拉取对应的音视频编码参数配置。
3. 添加角色和编解码参数配置<br/>

在“windows Web/ios/Android“ 三个tab下都选择“添加用户角色及配置”，每个tab下都添加如下三个角色。这三个角色对应互动直播里的开播，进房间和上麦三个场景。<br/>


* LiveMaster，类型选择 “主播“<br/><br/>
![添加角色](https://mc.qcloudimg.com/static/img/f3baf920bc8938dbf16dc5465f0a2253/jiaose.jpg)<br/><br/>
* Guest，类型选择 “观众“<br/><br/>
* LiveGuest,类型选择 “连麦观众“<br/>



如果开发者需要了解关于角色和参数的更详细说明，可以参考[这篇文档](https://github.com/zhaoyang21cn/suixinbo_doc/blob/master/SPEARConfig.md)。