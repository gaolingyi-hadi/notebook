## 描述
vuex是实现组件全局数据管理的一种机制,方便实现组件之间数据共享

## 好处
集中管理组件数据,方便维护

高效实现数据共享, 提高效率

数据都是响应式的,页面能保持数据同步
## 核心概念
* State 存放数据 是公共数据源 
    ```js
    //组件通过`this.$store.state`访问
    this.$store.state['dataName']

    //组件通过mapState 访问
    import {mapState} from 'vuex'
    computed:{
        ...mapState(['dataName'])
    }
    ```
* Mutation 存放函数 用于变更store中的数据 ,但是不能处理异步
    ```js
    //定义
    mutations:{
        functionName(){
            //修改 State 的代码
        }
    }
    ```
    ```js
    //组件通过`this.$store.commit`访问
    this.$store.commit("functionName")

    //组件通过 mapMutation 访问
    import {mapMutations} from 'vuex'
    methods:{
        ...mapMutations(['functionName'])
    }
    ```
* Action 存放函数 处理异步操作
    ```js
    //定义
    actions:{
        functionName(){
            //异步处理之后通过 context.commit 访问 Mutation 中的方法修改 state, 不能直接修改 state
            context.commit["functionName"]
        }
    }
    ```
    ```js
    //组件通过`this.$store.dispatch`访问
    this.$store.dispatch['functionName']

    //组件通过 mapActions 访问
    import {mapActions} from 'vuex'
    methods:{
        ...mapActions(['functionName'])
    }
    ```
* Getter 对 store 数据进行修改并返回新数据,不会直接改变原数据   
    ```js
    //定义
    getters:{
        functionName(){
            return '这是dataName' + state['dataName'] 
        }
    }
    ```
    ```js
    //组件通过`this.$store.commit`访问
    this.$store.getters ["functionName"]

    //组件通过 mapGetters 访问
    import {mapGetters} from 'vuex'
    computed:{
        ...mapGetters(['functionName'])
    }
    ```