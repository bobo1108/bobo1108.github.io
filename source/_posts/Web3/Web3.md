---
title: 区块链基础基础
catalog: true
date: 2024-04-06 10:26:40
subtitle:
header-img:
tags: 区块链
categories:	Web3
---

区块链基础
区块链白皮书 https://ethereum.org/zh/whitepaper/

## 课程大纲
### 比特币
#### 密码学基础
比特币被称为加密货币*（Crypto-currency）*，所有比特币用到了密码学中两个功能：
哈希和签名。
哈希有两个重要性质 
1. collision resistance（哈希碰撞）也称为 hash free（哈希碰撞）
哈希碰撞 ~ 找不到另外个m' 使得 h(m') = h(m) 
很著名的例子 MD5
2. hiding 指hash函数计算不可逆
这两个性质可以结合起来 可以实现digital commitment，也可称为digital equipment of a sealed envelope
例如预测股市，某某某预测明天某某股票涨停，问题在于预测结果公布会影响明日结果，类似于把预测结果放入第三方监管机构，第二天股市结果出来后打开，查看结果。
结合hash知识 x（预测结果） -> H(x) 把预测结果算出其hash值，并将其公布出去，因为cr性质，所以预测结果无法篡改。
实际中 H（x||nonce） 给输入加随机数，可以分布均匀
3. puzzle friendly H(x) hash值的计算事先是不可预测的，如果需要算出来的hash值是落在某个范围之内的，
为什么叫puzzle friendly？挖矿就是找随机数，nonce，使得H(x||nonce)落在某个范围之内。即H（block header）< target
挖矿过程没有捷径，不停试，找到符合条件的nonce；过程作为工作量的证明，（proof of work）
挖矿很难，验证很容易 diffucult to solove，but easy to verify
比特币用的hash算法是SHA256，secure hash algorithm

签名 要先看账户管理
去中心化 怎么开账户，创建公钥和私钥对，公私钥来源于非对称加密（asymmetric enryption algorithm）好处 公钥不用保密，私钥需要保密，解决秘钥分发不方便问题
公钥类似于账号，私钥类似于密码
公私钥是用来做签名的，公钥用来验证签名，私钥用来签名
比如我装10个比特币给你，交易发布到区块链上，别人怎么知道我发起的，我用私钥签个名，别人用公钥验证签名，验证通过，交易确认

#### 比特币的数据结构 
- 重要概念一：hash pointer ~ hash指针
普通的指针存的是某个结构体在内存中的地址
- 1.比特币中一个最基本的数据结构是区块链
区块链是什么？就是一个一个区块组成的链表
和普通的链表区别是什么？1、hash 指针代替普通指针，（不仅存储地址，还保存hash值）

![hash pointer](hash_pointer.png)
- 我们通过这样的数据结构实现tamper-evedent log
例如：有人篡改某个区块内容,通过hash指针找到篡改的区块，找到前一个区块，通过hash值判断是否篡改。

- 2.比特币中另一个数据结构是merkle tree，

![merkel-tree](merkel-tree.png)
binary tree，一个区别是hash 指针代替普通指针

每个区块分为block header 和 block body，这个区块包含的交易记录组成的merkel tree的根hash值存在这个区块的block header中，但是blokc header中不包含交易记录，只有根hash值，block body中包含交易列表。

merkel tree有什么用呢？
	- 1.找到这个交易所在的位置，从这个交易向上，找到根节点，这条路径就是merkel prooof
![merkel-proof](merkel-proof.png)

#### 比特币的协议







#### 共识协议和系统实现
#### 挖矿算法和难度调整
#### 比特币脚本
#### 软分叉和硬分叉
#### 匿名和隐私保护

### 以太坊
#### 概述-基于账户的分布式账本
#### 数据结构:状态树 交易树 数据树
#### GHOST协议
#### 挖矿 memory-hard mining puzzle
#### 挖矿难度调整
#### 权益证明
		Casper and Friendly Finality Gadget(FFG)
#### 智能合约
