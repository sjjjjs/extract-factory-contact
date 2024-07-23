## 第一步：采集地址

在供应商列表页面，使用 `F12`（Windows） 或 `Command + Shift + i` 打开开发者工具，选择“控制台”标签，复制并回车运行。

### 清除脚本

> 仅开始之前运行一次。

```js
// 清除缓存
;(function() {
    const k = '_$data';
    localStorage.removeItem(k);
    console.log('clear')
})();
```

### 缓存和复制脚本

> 每个分页都需要运行。

```js
// 保存并复制所有结果
;(function() {
    const k = '_$data';
    localStorage.setItem(k,`${localStorage.getItem(k) || ''}\n${Array.from($$('.factory-card')).map(i => i.querySelector('h3 a').href).join('\n')}`);
    copy(Array.from(localStorage.getItem(k).split('\n').map(i => i.trim()).filter(i => i).reduce((p, n) => p.add(n), new Set())).map(i => new URL(i).origin).join('\n'));
    console.log('copied')
})();
```

### 验证

重复操作完成后，使用 `ctrl + v` 可以输出所有地址列表，此时可以直接进入第二步。

## 第二步：采集信息

打开终端，输入命令并执行，等待结束后会在当前目录看到 `.csv` 文件，使用 Excel 打开可以查看数据。

```bash
npx cfl-cli@1.0.1
```

## 备注

### 安装 `node`

参考文档：https://www.runoob.com/nodejs/nodejs-install-setup.html

### 
