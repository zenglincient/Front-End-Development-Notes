store 使用的最佳实践
结合 createContext 和 useContext
```js
class Store = {
  constructor() {
    makeAutuObersver(this)
  }
}

const store = new Store()
const StoreContext = React.createContext(store)

<StoreContext.provide  value={store}>
  <children />
</StoreContext.provide>


const children = () => {
  const store = React.useContext(StoreContext)
  return <></>
}

```
## store 性能优化

1. autorun 要使用dispose 在组件卸载之后处理

```js
const CounterComponent = () => {
  useEffect(() => {
    const dispose = autorun(() => {
      document.title = `Count is ${counterStore.count}`;
    });

    return () => dispose(); // 组件卸载时清理
  }, []); // 空依赖数组确保effect只运行一次
```
2. 使用 reaction ，当长度变化的时候才执行 
```js
reation(store.list.length, () => {})
```
3. 使用 computed  (get)

4. 减少嵌套层级

5. 使用 runInAction 来合并更新
优化前代码
考虑以下代码，没有使用 runInAction 或事务，直接修改了多个可观察属性：
```js
import { makeAutoObservable } from "mobx";

class Store {
  count = 0;
  text = "Hello";

  constructor() {
    makeAutoObservable(this);
  }

  update() {
    this.count++;
    this.text = `Updated ${this.count}`;
  }
}

const myStore = new Store();

```
在这个例子中，调用 update 方法时，count 和 text 的更新将被视为两个独立的操作。如果有观察者依赖于 count 和 text，它们可能会因为这两次状态的改变而重新渲染两次。

优化后代码
现在，我们使用 runInAction 来合并这两次更新，确保相关的观察者只会在所有状态更新完成后重新计算和渲染一次：
```js
import { makeAutoObservable, runInAction } from "mobx";

class Store {
  count = 0;
  text = "Hello";

  constructor() {
    makeAutoObservable(this);
  }

  update() {
    runInAction(() => {
      this.count++;
      this.text = `Updated ${this.count}`;
    });
  }
}

const myStore = new Store();

```
优化的效果
减少重渲染次数：通过将多个状态更新合并为一个操作，避免了多次重渲染，从而提高了应用性能。
更有效的状态管理：runInAction 提供了一个清晰的方式来执行涉及多个状态更新的操作，使得代码更加易于理解和维护。
