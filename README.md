# bay-utils.js

> A Javascript Common Functions Library

This project is **working in progress**.

# Installation
## npm
```
$ npm install bay-utils.js
```

```js
import { isMobileUA } from 'bay-utils';
console.log(isMobileUA(navigator.userAgent));
> true;
```

## cdn

The easiest way to use utils is to load the built script:

```html
<!-- development -->
<script type="text/javascript" src="https://static.baydn.com/baydn/public/bay-utils/v1.1.6/bay-utils.js"></script>

<!-- production -->
<script type="text/javascript" src="https://static.baydn.com/baydn/public/bay-utils/v1.1.6/bay-utils.min.js"></script>
```

Having include the dependencies, the library can be used:

```js
xbayUtils.isMobileUA(navigator.userAgent);
```

# Usage

## Format

### parseDate
    /**
     * 获取一个日期对象
     * @param {string} time 日期
     * @return {Object} date 一个日期对象
     */
     const date = parseDate(time);

### formatDate
    /**
     * 获取某一格式的日期
     * @param {string} date 日期
     * @return {string} dateStr 格式为 y-m-d 的日期
     */
     const dateStr = formatDate(date);

### formatSafetyStr
    /**
     * 获取一部分为明文的字符串
     * @param {string} str 字符串
     * @param {number} start 截取字符串符号的开始位置，从字符串开始计算，以 1 开始
     * @param {number} end 截取字符串符号的结束位置，从字符串结尾计算，以 1 开始
     * @param {string} symbol 截取字符串符号，默认为 *
     * @return {string} str 一部分为明文的字符串，比如：1****com
     */
     > formatSafetyStr('12345com', 1, 3);
     > '1****com'

### formatSafetyEmail
    /**
     * 获取一部分为明文的邮箱地址
     * @param {string} email 邮箱地址
     * @param {number} start 同 formatSafetyStr，默认值为邮箱地址长度的 1/4
     * @param {number} end 同 formatSafetyStr，默认值为邮箱地址长度的 1/4
     * @param {string} symbol 截取字符串符号，默认为 *
     * @return {string} str 一部分为明文的邮箱地址，比如：1****com
     */
     > formatSafetyEmail('1234567@qq.com')
     > '123********com'

### formatSafetyMobilephone
    /**
     * 获取一部分为明文的电话号码
     * @param {string} mobilephone 电话号码
     * @param {number} start 同 formatSafetyStr，默认值为 3
     * @param {number} end 同 formatSafetyStr，默认值为 4
     * @param {string} symbol 截取字符串符号，默认为 *
     * @return {string} str 一部分为明文的电话号码，比如：181****3344
     */
     > formatSafetyMobilephone('18111223344');
     > '181****3344'

## Validator

### assertString
    验证输入是否是字符串
    > assertString(111)
    > false

### toString
    > toString({x: 1})
    > false

### merge
    合并两个 object，第二个参数的 key 不会覆盖前面的。
    > merge({x: 1}, {x: 2, y: 4})
    > false

### isStandardBrowserEnv
    判断是否是标准的浏览器环境
    > isStandardBrowserEnv()
    > false

### isFunction
    > isFunction(function(){})
    > true

### isWechatUA
    判断 Agent 是否是微信
    > isWechatUA(navigator.userAgent)
    > false

### isMobileUA
    判断 Agent 是否是手机
    > isMobileUA(navigator.userAgent)
    > false

### isAndroidUA
    判断 Agent 是否是 Android
    > isAndroidUA(navigator.userAgent)
    > false

### isIOSUA
    判断 Agent 是否是 iOS
    > isIOSUA(navigator.userAgent)
    > false

### isShanbayAppUA
    判断 Agent 是否是扇贝 APP
    > isShanbayAppUA(navigator.userAgent)
    > false

### isMobilePhone
    判断字符串是否是手机号
    > isMobilePhone(13323432221)
    > true

### isEmail
    判断字符串是否是邮箱
    > isEmail('133@qq.com')
    > true

### isUrl
    判断字符串是否是 url
    > isUrl('https://www.shanbay.com/')
    > true

### escapeStr
    转义 <, >, &, ', " 和 /。
    > escapeStr('<p>hi</p>')
    > "&lt;p&gt;hi&lt;&#x2F;p&gt;"

### unescapeStr
    > unescapeStr("&lt;p&gt;hi&lt;&#x2F;p&gt;")
    > "<p>hi</p>"

### isStrLength
    第二个参数是 options，默认为 {min:0, max: undefined}
    > isStrLength('hello', {min: 2, max: 5})
    > true

### isJSON
    判断字符串是不是 json，使用 json.parse
    > isJSON('hello')
    > false
    > isJSON(JSON.stringify({x: 1}))
    > true

### isNumeric
    判读字符串是否为数字
    > isNumeric('123');
    > true

### isEmptyStr
    判断字符串是否为空
    > isEmptyStr('123');
    > false

## Dom

### hasClass
    /**
     * 判断元素是否有某个 class
     * @param {element} el 元素
     * @param {string} className
     * @return {boolean}
     */
    hasClass(el, 'foo');

### addClass
    /**
     * 给元素添加某个 class
     * @param {element} el 元素
     * @param {string} className 添加的 class
     */
    addClass(el, 'foo');

### removeClass
    /**
     * 给元素删除某个 class
     * @param {element} el 元素
     * @param {string} className 删除的 class
     */
    removeClass(el, 'foo');

### getFormData
    /**
     * 获取表单数据
     * @param {element} formEl 表单元素
     * @return {Object} data 表单中 name 有值的输入框的数据，数据结构与 FormData 相同。
                        当输入框 type 为 radio 的时候，只返回选中状态的值。
     */
     const data = getFormData(formEl);

### clearFormData
    /**
     * 清空表单输入框的值
     * @param {element} formEl 表单元素
     */
     clearFormData(formEl);

### selectElement
    /**
     * 选择元素中的内容
     * @param {element} el 元素
     */
     selectElement(el);

### copyToClipboard
    /**
     * 复制文字到剪贴板
     * @param {string} text 复制的内容
     */
     copyToClipboard(text);

### lazyloadImage
    /**
     * 图片懒加载
     */
     lazyloadImage();

### countDownBtn
    /**
     * 按钮倒计时
     * @param {element} el 按钮元素
     * @param {object} options 选项，具体如下：
     *    time： 倒计时时间，默认为 60，单位为 s
     *    getProcessText： 倒计时时每隔 1s 的调用，传入倒计时剩余的秒数，返回需要显示的文字，默认为 countDownTime  => `${countDownTime}s后重发`,
     *    endText： 倒计时结束的文字，默认为'重新获取验证码'
     * @return {string} cdInterval 倒计时标记
    **/


## Others

### ajax
    /**
    * @param {string} options 类似 jquery ajax 的 options。
    * 不同的是当 isOriginal 为 false 时，success 判断了 status_code 为 0，success 会返回 data，
    * 而 error 是在请求失败时调用的(包括 status_code 不为 0)，会返回 status 和 msg 两个参数。
    * @param {string} isOriginal 为 true 时，将不会对 success 和 error 做任何处理，默认为 false
    * @param {object} configure 当 key 为 LOGIN_URL 时，值是请求 401 或 403 时 redirect 的 url，默认为 '/accounts/login'。
    */
    ajax(options, isOriginal, configure);

### getSearchValue
    /**
    * 获取链接中 search 的值
    * @param {string} name 名称
    * @param {string} url 链接，默认为当前链接
    */
    const value = getSearchValue(name);

### getCookie
    /**
    * 获取 cookie 中的值
    * @param {string} cookie 名称
    * @param {string} name 名称
    */
    const value = getCookie(cookie, name);

### uniqArr
    /**
    * 对 array 去重
    * @param {Array} 原数组
    * @return {Array} 新数组
    */
    const newArr = uniqArr(arr);

### getUrlsFromStr
    /**
    * 获取 string 中的 urls
    * @param {String} 字符串
    * @return {Array} 包含 url 的数组
    */
    const urlsArr = getUrlsFromStr(str);

### transformUrlToAnchor
    /**
    * 将字符串中的 url 转化成 html 中的 a 元素
    * @params {String} 字符串
    * @return {String} 包含 a 元素的字符串
    */
    const newStr = transformUrlToAnchor(str);
