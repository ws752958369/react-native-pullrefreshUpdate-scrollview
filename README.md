# react-native-pullrefreshUpdate-scrollview
react-native上拉或下拉刷新组件
用法示例：支持有IOS导航栏的情况
import PullRefreshScrollView from 'react-native-pullrefresh-scrollview'

    onRefresh(PullRefresh) {
        setTimeout(()=>{

            this.state.data.splice(0,0,{title:'张三李四',text:'哇哇哇哇哇'});

            this.setState({dataSource:this.state.ds.cloneWithRows(this.state.data),load:true});
            PullRefresh.onRefreshEnd();

        }, 2000);
    }

    onLoadMore(PullRefresh) {
        setTimeout(()=>{

            this.state.data.push({title:'张三李四王五',text:'哇哇哇哇哇'});

            this.setState({dataSource:this.state.ds.cloneWithRows(this.state.data),load:true});
            //PullRefresh.onLoadMoreEnd();

        }, 2000);
    }

    render() {
        return (
            <ListView dataSource={this.state.dataSource}
                      renderRow={(rowData, sectionID, rowID, highlightRow)=>this.renderRow(rowData, sectionID, rowID, highlightRow)}
                      renderScrollComponent={(props)=><PullRefreshScrollView onRefresh={(PullRefresh)=>this.onRefresh(PullRefresh)}   onLoadMore={(PullRefresh)=>this.onLoadMore(PullRefresh)} useLoadMore={1}{...props} />}
            />
        )
    }
