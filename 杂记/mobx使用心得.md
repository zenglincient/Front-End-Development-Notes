store 使用的最佳实践
结合 createContext 和 useContext
class Store = {
  constructor() {
    makeAutuObersver(this)
  }
}

const store = new Store()
const StoreContext = React.createContext(store)

<StoreContext.provide >
  <children />
</StoreContext.provide>


const children = () => {
  const store = React.useContext(StoreContext)
  return <></>
}
