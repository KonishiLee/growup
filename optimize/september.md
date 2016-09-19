#  WEB优化 - 九月



#### 1.详情列表预研

*   解决问题：
在模块中列表到详情，修改之后，返回列表需要到以前的状态，但是数据要更新为最新状态，页面是不能刷新的，方便与用户的操作。

*    解决方案：
  将Stack的思想用于在View当中，然后保证页面不能刷新，在内存当中更新数据。

*  时间：
  9-19已经发布了一个能支持的版本，只是实现了功能，还需要继续优化，将这一块统一管理，写一个公共库。

#### 2.富文本预研

这个需要服务端，移动端进行统一开发，移动端需要支持View。

#### 3.Css模块化

*  解决问题：
  现在Css代码比较冗余，出现重复，僵尸代码情况，造成Css不好维护，以及最后编译文件过大。
*  解决方案：
  首先将Css分为三大类，Global，Component，Module，分片管理维护。
*  时间：
  长线优化

#### 4.Js组件化

*  解决问题：
  当项目越来越大，需要考虑的问题是最后打包之后的文件能尽量减少重写，增加复用，并且现在的模块之间很多相似的地方，为了更好的维护，需要做一个整体上的调整。

*  解决方案：
  将以前框架上以Module的思想改变为 Component + Module 的形式，实现组件化的方式，提高组件的使用潜力，更加方便维护以及减少重复书写。

*  时间：
  目前已经修改部分，属于长线工作

#### 5.系统配置可操作性

*  解决问题：
  各种时间Format，PageSize等，在产品提出需要快速更改的情况下，前端能够响应最快速度进行修改。

*  解决方案：
  封装一个Config文件，定义一些基础的配置，各模块需要调用这一底层文件。

*  时间：
  时间Format在View中呈现已经大致修改完成，还有一部分需要与服务端，移动端进行统一。