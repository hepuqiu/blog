---
title: 浅谈JS防抖和节流
date: 2019-11-22 10:17:27
tags:
---
# 浅谈JS防抖和节流
在窗口scroll、resize,输入框内容改变时，需要对调用事件处理函数的频率加以限制，如果放任不管或处理不当，可能大量消耗浏览器资源，甚至导致浏览器卡死，带来非常差的用户体验。此时，我们可以采用防抖(debounce)和节流(throttle)来限制事件处理函数调用频率。
## 防抖(debounce)
**定义**：设定一个时间段，当持续触发事件时，上一次触发事件后，一定时间内没有继续触发事件，才会调用事件处理函数；在给定时间段之前又一次触发了事件，就重新延时。

简单的debounce实现
```javascript
/***
*@param {Function} fn 需要进行防抖的函数
*@param {number} delay 防抖时间间隔，毫秒
**/
const debounce = (fn, delay) => {
	let timeout = null;
	return (...args) => {
		const self = this;
		if (timeout) {
			clearTimeout(timeout); // 计时过程中再次触发事件，清除计时器，重新计时
		}
		timeout = setTimeout(() => {
			fn.apply(self, args);
		}, delay || 500);
	};
};
```
**效果**： 当持续触发事件，时间间隔都小于设定时间段时，只会在最后执行一次事件处理函数。
## 节流(throttle)
**定义**：设定一个时间段，当持续触发事件时，每间隔一段时间，调用一次事件处理函数。就像字面意思一样，将调用事件处理函数的频率减小。
简单的throttle实现
```javascript
/***
*@param {Function} fn 需要进行节流的函数
*@param {Number} delay 时间间隔，毫秒
**/
const throttle = (fn, delay) => {
	let pre = Date.now();
	return (...args) => {
		const self = this;
		const now = new Date();
		if (now - pre > delay) { // 判断时间间隔是否大于给定时间来执行事件处理函数
			fn.apply(self, args);
			pre = now; // 当前函数执行时的时间作为计算下次函数执行时间的起始时间
		}
	};
};
```
**效果**： 当持续触发事件时，每隔一段时间，执行一次事件处理函数。

## 对比
当两者的触发条件完全一致，设定的时间间隔也一致，且触发时间都小于设定的时间时，函数防抖只会在最后执行一次事件处理函数，函数节流固定且持续的在设定的时间段内执行一次
