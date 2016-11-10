# GitFlow开发流程

> _**随着团队的扩大，【功能分支工作流】这种开发模式可能不再适合敏捷，中型团队了。所以引入 -- `GitFlow`**_



### Working Flow

* 功能分支工作流

* Forking

* GitFlow

* PullRequests

* ...

> _当然也有其他的一些开发模式，也有互相配合的，这里就不详细讲了。_

### Branch

* `master`

  用于**产品环境**，不能被污染

* `develop`

  用于**测试环境**，所有的新功能都通过该分支checkout

* `hotfix`

  用于**产品环境热修复**，当产品环境突然出现bug，应该通过master分支checkout到hotfix，进行紧急修复

* `release`

  用于**测试环境热修复**，内部测试环境出现错误，应该通过develop分支checkout到release，进行修复

* `staging`

  用于**发布测试环境**，不能随便merge与push

* `feature/**`

  用于**功能迭代**，命名大概分为 1.feature/xx 2.feature_xx ...





### 图片参考


![有图参考](https://raw.githubusercontent.com/quickhack/translations/master/git-workflows-and-tutorials/images/git-workflow-release-cycle-4maintenance.png)




