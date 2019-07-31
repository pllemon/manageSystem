
<template>
    <div class="nav-tabs flex" style="width:100%;">
        <p class="menu-btn">菜单栏</p>
        <div class="flex1" style="overflow:hidden">
            <el-tabs v-model="activeTab" type="card" closable @tab-remove="removeTab" class="main-tabs">
                <el-tab-pane
                    v-for="(item) in editableTabs2"
                    :key="item.name"
                    :label="item.title"
                    :name="item.name"
                >
                </el-tab-pane>
            </el-tabs>
        </div>
        <el-dropdown class="tabs-action">
            <span class="el-dropdown-link">
                <span>操作</span>
                <i class="el-icon-arrow-down el-icon--right"></i>
            </span>
            <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>刷新当前</el-dropdown-item>
                <el-dropdown-item>关闭全部</el-dropdown-item>
            </el-dropdown-menu>
        </el-dropdown>
    </div>
</template>
<script>
    export default {
        data() {
        return {
            activeTab: '2',
            editableTabs2: [{
                title: 'Tab 1',
                name: '1',
                content: 'Tab 1 content'
            }, {
                title: 'Tab 2',
                name: '2',
                content: 'Tab 2 content'
            }],
            tabIndex: 2
        }
        },
        methods: {
            addTab(targetName) {
                let newTabName = ++this.tabIndex + '';
                this.editableTabs2.push({
                title: 'New Tab',
                name: newTabName,
                content: 'New Tab content'
                });
                this.activeTab = newTabName;
            },
            removeTab(targetName) {
                let tabs = this.editableTabs2;
                let activeName = this.activeTab;
                if (activeName === targetName) {
                tabs.forEach((tab, index) => {
                    if (tab.name === targetName) {
                    let nextTab = tabs[index + 1] || tabs[index - 1];
                    if (nextTab) {
                        activeName = nextTab.name;
                    }
                    }
                });
                }
                this.activeTab = activeName;
                this.editableTabs2 = tabs.filter(tab => tab.name !== targetName);
            }
        }
    }
</script>

<style lang="scss">
.main-tabs{
    .el-tabs__nav-scroll{
        background: #fff;
    }
    .el-tabs__header{
        margin: 0;
    }
}
</style>
<style scoped lang="scss">
.nav-tabs{
    background: #fff;
    border-bottom: 1px solid #dcdcdc;
    align-items: center;
    .menu-btn{
        padding: 0 10px;
    }
    .tabs-action{
        padding: 0 10px;
    }
}
</style>
