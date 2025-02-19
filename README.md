[![pinyin-pro Logo](https://i.ibb.co/26fJ5vF/pinyin-logo.png)](https://github.com/zh-lx/pinyin-pro)

[![NPM version](https://img.shields.io/npm/v/pinyin-pro.svg)](https://www.npmjs.com/package/pinyin-pro)
[![GITHUB star](https://img.shields.io/github/stars/zh-lx/pinyin-pro.svg)](https://github.com/zh-lx/pinyin-pro)
[![travis-build](https://travis-ci.com/zh-lx/pinyin-pro.svg?branch=main)](https://travis-ci.com/github/zh-lx/pinyin-pro)
[![NPM Downloads](https://img.shields.io/npm/dm/pinyin-pro.svg)](https://npmcharts.com/compare/pinyin-pro?minimal=true)
[![Coverage Status](https://coveralls.io/repos/github/zh-lx/pinyin-pro/badge.svg?branch=main)](https://coveralls.io/github/zh-lx/pinyin-pro?branch=main)
[![MIT-license](https://img.shields.io/npm/l/pinyin-pro.svg)](https://opensource.org/licenses/MIT)
[![GITHUB-language](https://img.shields.io/github/languages/top/zh-lx/pinyin-pro.svg)](https://github.com/zh-lx/pinyin-pro)

## 特色功能

- 支持汉字、词语、句子多种格式输入获取
- 获取拼音
- 获取声母
- 获取韵母
- 获取拼音首字母
- 获取音调
- 获取多音字的多种拼音
- 支持字符串和数组两种输出形式

## 版本更新

当前版本： 3.2.0 -> 3.2.1

- 修复部分单字的常用读音<br>
  - 艾: 'yì' -> 'ài yì'
  - 吽: 'ōu' -> 'hōng hǒu ōu'

点击查看 [版本更新文档](./CHANGELOG.md)

## 安装

npm 安装

```
npm install pinyin-pro
```

yarn 安装

```
yarn add pinyin-pro
```

## 引入

浏览器 script 引入:

```html
<!--引入某个版本，如3.2.0版本-->
<!-- <script src="https://cdn.jsdelivr.net/gh/zh-lx/pinyin-pro@3.2.0/dist/pinyin-pro.js"></script> -->
<!--引入最新版本-->
<script src="https://cdn.jsdelivr.net/gh/zh-lx/pinyin-pro@latest/dist/pinyin-pro.js"></script>
<script>
  var { pinyin } = pinyinPro;
  pinyin('汉语拼音'); // 'hàn yǔ pīn yīn'
</script>
```

ESModule 引入：

```javascript
import { pinyin } from 'pinyin-pro';
pinyin('汉语拼音'); // 'hàn yǔ pīn yīn'
```

commonjs 引入：

```javascript
const { pinyin } = require('pinyin-pro');
pinyin('汉语拼音'); // 'hàn yǔ pīn yīn'
```

## 参数

`pinyin(word, options)` 接收两个参数<br>

- <b>word：</b>必填。String 类型，需要转化为拼音的中文
- <b>options：</b>可选。Object 类型，用于配置各种输出形式，options 的键值配置如下：

| 参数     | 说明                                                          | 类型    | 可选值                                 | 默认值 |
| -------- | ------------------------------------------------------------- | ------- | -------------------------------------- | ------ |
| pattern  | 输出的结果的信息（拼音 / 声母 / 韵母 / 音调 / 首字母）        | string  | pinyin / initial / final / num / first | pinyin |
| toneType | 音调输出形式(拼音符号 / 数字 / 不加音调)                      | string  | symbol / num / none                    | symbol |
| type     | 输出结果类型（字符串/数组）                                   | string  | string / array                         | string |
| multiple | 输出多音字全部拼音（仅在 word 为长度为 1 的汉字字符串时生效） | boolean | true / false                           | false  |

## 使用示例

### 获取拼音

```js
import { pinyin } from 'pinyin-pro';

// 获取带音调拼音
pinyin('汉语拼音'); // 'hàn yǔ pīn yīn'
// 获取不带声调的拼音
pinyin('汉语拼音', { toneType: 'none' }); // 'han yu pin yin'
// 获取声调转换为数字后缀的拼音
pinyin('汉语拼音', { toneType: 'num' }); // 'han4 yu3 pin1 yin1'
// 获取数组形式带音调拼音
pinyin('汉语拼音', { type: 'array' }); // ["hàn", "yǔ", "pīn", "yīn"]
// 获取数组形式不带声调的拼音
pinyin('汉语拼音', { toneType: 'none', type: 'array' }); // ["han", "yu", "pin", "yin"]
// 获取数组形式声调转换为数字后缀的拼音
pinyin('汉语拼音', { toneType: 'num', type: 'array' }); // ["han4", "yu3", "pin1", "yin1"]
```

### 获取声母

```js
import { pinyin } from 'pinyin-pro';

// 获取声母
pinyin('汉语拼音', { pattern: 'initial' }); // 'h y p y'
// 获取数组形式声母
pinyin('汉语拼音', { pattern: 'initial', type: 'array' }); // ["h", "y", "p", "y"]
```

### 获取韵母

```js
import { pinyin } from 'pinyin-pro';

// 获取带音调韵母
pinyin('汉语拼音', { pattern: 'final' }); // 'àn ǔ īn īn'
// 获取不带音调韵母
pinyin('汉语拼音', { pattern: 'final', toneType: 'none' }); // 'an u in in'
// 获取音调为数字的韵母
pinyin('汉语拼音', { pattern: 'final', toneType: 'num' }); // 'an4 u3 in1 in1'
// 获取数组形式带音调韵母
pinyin('汉语拼音', { pattern: 'final', type: 'array' }); // ["àn", "ǔ", "īn", "īn"]
// 获取数组形式不带音调韵母
pinyin('汉语拼音', { pattern: 'final', toneType: 'none', type: 'array' }); // ["an", "u", "in", "in"]
// 获取数组形式音调为数字的韵母
pinyin('汉语拼音', { pattern: 'final', toneType: 'num', type: 'array' }); // ['an4', 'u3', 'in1', 'in1']
```

### 获取音调

```js
import { pinyin } from 'pinyin-pro';

// 获取音调
pinyin('汉语拼音', { pattern: 'num' }); // '4 3 1 1'
// 获取数组形式音调
pinyin('汉语拼音', { pattern: 'num', type: 'array' }); // ["4", "3", "1", "1"]
```

### 获取拼音首字母

```js
import { pinyin } from 'pinyin-pro';

// 获取拼音首字母
pinyin('赵钱孙李额', { pattern: 'first' }); // 'z q s l é'
// 获取不带音调拼音首字母
pinyin('赵钱孙李额', { pattern: 'first', toneType: 'none' }); // 'z q s l e'
// 获取数组形式拼音首字母
pinyin('赵钱孙李额', { pattern: 'first', type: 'array' }); // ['z', 'q', 's', 'l', 'é']
// 获取数组形式不带音调拼音首字母
pinyin('赵钱孙李额', { pattern: 'first', toneType: 'none'， type: 'array' }); // ['z', 'q', 's', 'l', 'e']
```

### 获取单个字的多音

只有单字可以获取到多音模式, 词语、句子无效。同样可以通过配置 options 选项获取数组形式、韵母等格式

```javascript
import { pinyin } from 'pinyin-pro';

// 获取多音
pinyin('好', { multiple: true }); // 'hǎo hào'
// 获取数组形式多音
pinyin('好', { multiple: true, type: 'array' }); // ["hǎo", "hào"]
```

## 贡献与反馈

使用遇到问题或者需要功能支持欢迎提 issue。

交流及参与贡献欢迎加微信：

![wechat](https://i.ibb.co/VYXW19H/QQ-20210323221842.jpg)
