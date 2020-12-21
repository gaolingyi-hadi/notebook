## computed 和 watch 的区别
### computed
* computed 是计算属性,它会根据你所依赖的数据动态显示新的计算结果,并且缓存
* 计算属性默认只有 getter,不过在需要时你也可以提供一个 setter

### watch
 watch 是监听器, 依赖的数据发生改变时执行一个函数(包括异步操作),并在我们得到最终结果前 ,设置中间状态

 ### .sync 修饰符
 在有些情况下,我们可能需要对一个 prop 进行“双向绑定”.不幸的是,真正的双向绑定会带来维护上的问题,因为子组件可以变更父组件,且在父组件和子组件都没有明显的变更来源.所以推荐子组件调用父组件提供的函数来改变父组件数据.

 ```xml
    <my-div :title="title" @update:title="(res)=>(title = res)"></my-div>

    <!-- 约定好给组件使用的函数以 'update:'开头 -->
    <!-- 再使用.sync语法糖后 -->
    <my-div :title.sync="title"></my-div>
 ```
