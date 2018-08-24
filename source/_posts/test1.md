---
title: 2017-11-9 Ruby中的nil?, empty?与Rails中的blank?, present?区别
categories: server
tags: ruby
---

[TOC]

### nil?
`.nil?` 可以用在一切对象上，当对象为nil时，返回true
意思就是当前的对象为null时，这个方法的返回值为true
```
if user.nil?
	user = User.new(original_user.attributes.except("customer_id"))
	user.save(:validate => false)
end
```
### empty?
`.empty?` 可以用在字符串，数组或者哈希，当满足下列条件时，返回true
```
· String length == 0
· Array length == 0
· Hash length == 0
```
注意：在nil对象上调用`.empty?`会抛出`NoMethodError`异常
### blank?
`.blank?`就是为了解决nil对象上调用empty的尴尬问题，这个方法是rails实现的，类似于`.empty?`可以作用于字符串，数组或者哈希，`.blank?`可以作用于认为对象
```
nil.blank? == true
false.blank? == true
[].blank? == true
{}.blank? == true
"".blank? == true
5.blank? == false
0.blank? == false
```
对于只包含空格的字符串，`.blank?`的返回同样为true，这个区别与`.empty?`
```
"  ".blank? == true
"  ".empty? == false
```
### present?
Rails同样提供了`.present?`方法，其返回值与`.blank?`相反
注意：就算数组中的元素都为blank时，对数组调用`.blank?`仍然会返回false。对于这种情况时，使用`.all?`配合`.blank?`，如下例：
```
[nil, ""].blank? == false
[nil, ""].all? &:blank? == true
```