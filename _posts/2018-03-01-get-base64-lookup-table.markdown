---
layout: post
title:  "Get Base64 Lookup Table"
date:   2018-03-02 09:01:57 +0800
categories: [Tool]
desc: "a tool to get base64 lookup table"
tags: [base64,encoding]
keywords: "base64"
icon: icon-html
---
Generate a byte array and passed to a base64 encoder,the return result is the lookup table.
What I am doing is to generate a byte array which will be encoded to a index array like 
[0,1,2,3...,63],so the encoding result is the look up table,see [wiki][base_64].
```
byte[] tmp = new byte[48];
for (byte i = 0, j = 0; i < 64; i += 4, j += 3) {
    tmp[j] = (byte) (((i & 0x3f) << 2) | (((i + 1) & 0x3f) >>> 4));
    tmp[j + 1] = (byte) ((((i + 1) & 0x3f) << 4) | (((i + 2) & 0x3f) >>> 2));
    tmp[j + 2] = (byte) ((((i + 2) & 0x3f) << 6) | ((i + 3)) & 0x3f);
}
```
[base_64]: https://en.wikipedia.org/wiki/Base64
