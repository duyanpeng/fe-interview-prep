# react
## 链接
[React 技术揭秘](https://kasong.gitee.io/just-react/preparation/source.html)  

[React18](https://blog.csdn.net/zgd826237710)  

[精读 React18](https://zhuanlan.zhihu.com/p/388891604)  

[Batch Update 浅析](https://zhuanlan.zhihu.com/p/28532725)  

[React合成事件系统](https://zhuanlan.zhihu.com/p/25883536)  

## 文档备忘录

### 生命周期
```
从Reactv17开始，componentWillXXX钩子前增加了UNSAFE_前缀。

究其原因，是因为Stack Reconciler重构为Fiber Reconciler后，render阶段的任务可能中断/重新开始，对应的组件在render阶段的生命周期钩子（即componentWillXXX）可能触发多次。这种行为和Reactv16不一致，所以标记为UNSAFE_。

为此，React提供了替代的生命周期钩子getSnapshotBeforeUpdate。

我们可以看见，getSnapshotBeforeUpdate是在commit阶段内的before mutation阶段调用的，由于commit阶段是同步的，所以不会遇到多次调用的问题。
```