## 调用Render会发生什么？（下面是简答版本）
ReactDOM.render()
├─ 创建 FiberRoot 和 ReactRoot
├─ 启动 updateContainer
│   ├─ 协调阶段（构建 Fiber 树）
│   │   ├─ beginWork（处理组件）
│   │   └─ completeWork（收集副作用）
│   └─ 提交阶段（更新 DOM）
│       ├─ BeforeMutation
│       ├─ Mutation（DOM 操作）
│       └─ Layout（生命周期）
└─ 回调函数执行

1. 首先，我们写的是JSX，会被编译成React.createElement. 也就是Render(ReactElement, 节点元素)
2. 判断有没有根节点 legacyRenderSubtreeIntoContainer ，如果没有，就通过 createLegacyRoot 先创建根Fiber节点。
3. 如果有，或者创建完之后，调用 `updateContainer` 方法。就是通过ReactElement去创建Fiber
4. updateContainer 会标记一些优先级，核心是 调用 `scheduleUpdateOnFiber`
5. `scheduleUpdateOnFiber` 做了什么？ 1.检查有没有嵌套，2. 先回溯，找到根节点，3.17版本源码里有一些检查同步更新的逻辑。检查如果是同步更新，performSyncWorkOnRoot
6. performSyncWorkOnRoot 经过一些函数，调用 workLoopSync ，循环调用 performUnitOfWork
7. performUnitOfWork 是工作单元，通过他去调用 beginWork 去完成
8. beginWork 这里就开始进入react diff与创建fiber树的过程了（详见下面的diff过程）
9. completeWork 处理副作用
