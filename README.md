## 第一步：采集地址

```js
// 清除缓存
;(function() {
    const k = '_$data';
    localStorage.removeItem(k);
    console.log('clear')
})();
```

```js
// 保存并复制所有结果
;(function() {
    const k = '_$data';
    localStorage.setItem(k,`${localStorage.getItem(k) || ''}\n${Array.from($$('.factory-card')).map(i => i.querySelector('h3 a').href).join('\n')}`);
    copy(Array.from(localStorage.getItem(k).split('\n').map(i => i.trim()).filter(i => i).reduce((p, n) => p.add(n), new Set())).map(i => new URL(i).origin).join('\n'));
    console.log('copied')
})();
```

## 第二步：采集信息


## 备注

### 安装 `node`

参考文档：https://www.runoob.com/nodejs/nodejs-install-setup.html

### 
