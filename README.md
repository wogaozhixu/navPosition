# Navigation Precise Position

This project is base on [Ant Design Pro](https://pro.ant.design). it works with the history url. If you have similar business requirements, please feel free to use this feature

## Environment Prepare

Install `node_modules`:

```bash
npm install
```

or

```bash
yarn
```

### Start project

```bash
npm start
```

or

```bash
yarn start
```

### keys

```bash
// 根据路径判断当前激活状态的导航
getMenuName = () => {
  const pathname = this.props.history.location.pathname.replace('/', '');
  const currentPath =
    pathname.indexOf('/') > 0 ? pathname.slice(0, pathname.indexOf('/')) : pathname;
  const currentSlider =
    pathname.lastIndexOf('/') > 0
      ? pathname.slice(pathname.lastIndexOf('/') + 1, pathname.length)
      : pathname;
  this.setState({
    current: currentPath,
    currentSlider,
  });
};
// 监听pathname并生成对应左侧导航
const renderSliderMenu = () => {
  const pathName = history.location.pathname;
  const menuDoms = [];
  const currentData = sliderMenuData.filter(t => pathName.indexOf(`${t.sourcePath}`) > 0);
  currentData.map(item => {
    const dom = (
      <Menu.Item key={item.key} onClick={() => history.push(item.url)}>
        <Icon type={item.type} />
      </Menu.Item>
    );
    return menuDoms.push(dom);
  });
  return menuDoms.length > 0 ? (
    <Sider width={50} style={{ position: 'absolute', top: 50, background: '#fff' }}>
      <Menu
        mode="vertical"
        className={styles.calcMenuHeight}
        onClick={this.getMenuName}
        selectedKeys={[currentSlider]}
      >
        {menuDoms}
      </Menu>
    </Sider>
  ) : (
    ''
  );
};
```

### Tips

```bash
if you want to see more about the feature, you can get it in 'src/layout/BlankLayout'.
Welcome all talents to complete this feature！
```


