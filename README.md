<!--
 * @Author: robert zhang <robertzhangwenjie@gmail.com>
 * @Date: 2022-11-12 12:05:59
 * @LastEditTime: 2023-02-27 22:05:44
 * @LastEditors: robert zhang
 * @Description: 
-->
# Gitbook2Pdf 
## This project has solved the image display problem   
- 原因分析  
  当页面图片的地址为相对地址时，因为拼接的baseUrl为传入的url，因此当gitbook存在多个子章节时，子章节中的img url拼接错误  
- 解决方案  
  再爬取每个章节的内容后，将内容中的所有img标签中的属性scr进行替换，使用urllib.parse.urljoin替换为当前章节的所有img属性src的值

## Features

- Asynchronous fetching
  Uses `aiohttp` for fetching
  Can fetch the entire site in seconds

- Generated text can be copied
  ![](./screenshots/copy-feature.png)
- Preserves original directory structure
  ![](./screenshots/index.png)

- Maintains original hyperlinks
  ![](./screenshots/link-feature.png)

- Preserves original site formatting (cannot fetch content rendered by JavaScript 🤷‍♂️)
- Minimal storage space usage, an 800-page PDF file only takes up 4.6MB

### Sample File

[KubernetesHandbook.pdf](http://cdn2.xhyuan.co/KubernetesHandbook.pdf)

## Installation

### Please Note!

**Since it requires `weasyprint` to generate `pdf`, and `pip` cannot install `weasyprint`, you need to install it manually.**
Here is the [installation guide](https://weasyprint.readthedocs.io/en/latest/install.html#linux) for `weasyprint`.
If you don't want to install dependencies, you can use the [docker image](https://github.com/soulteary/docker-gitbook-pdf-generator) provided by `soulteary`.

```sh
pip install -r requirements.txt
```

## Usage 
### With Docker
```shell
docker run -it -v `pwd`/output:/app/output zhangwenjie/gitbook2pdf <your url> <filename.pdf>
```

### With python
```shell
pip install -r requirements.txt
python gitbook.py <url> <filename.pdf>
```

## Customization

The generated `pdf` style depends on the `css` file. If you need to add other styles, you can do so by modifying the `gitbook.css` file.

## Original Project
[original project url](https://github.com/fuergaosi233/gitbook2pdf)

## Warning ⚠️

Using `weasyprint` to generate PDF files will consume a large amount of memory.
So please ensure you have enough memory space to generate the files.
