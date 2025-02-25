---
title: 安装 Git Large File Storage
intro: '为使用 {% data variables.large_files.product_name_short %}，您需要下载并安装不同于 Git 的新程序。'
redirect_from:
  - /articles/installing-large-file-storage
  - /articles/installing-git-large-file-storage
  - /github/managing-large-files/installing-git-large-file-storage
  - /github/managing-large-files/versioning-large-files/installing-git-large-file-storage
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
shortTitle: Install Git LFS
ms.openlocfilehash: b7078a3147ed610ff67bdc4b0bdce93158279a94
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: '145129245'
---
{% mac %}

1. 导航到 [git-lfs.github.com](https://git-lfs.github.com) 并单击“下载”。 也可以使用包管理器安装 {% data variables.large_files.product_name_short %}：
    - 要使用 [Homebrew](http://brew.sh/)，请运行 `brew install git-lfs`。
    - 要使用 [MacPorts](https://www.macports.org/)，请运行 `port install git-lfs`。

 如果安装用于 Homebrew 或 MacPorts 的 {% data variables.large_files.product_name_short %}，请跳至步骤 6。

2. 在计算机上，找到并解压缩下载的文件。
{% data reusables.command_line.open_the_multi_os_terminal %}
3. 将当前工作目录更改为您下载并解压缩的文件夹。
  ```shell
  $ cd ~/Downloads/git-lfs-<em>1.X.X</em>
  ```
 {% note %}

 **注意：** 在 `cd` 后面使用的文件路径取决于你的操作系统、下载的 Git LFS 版本以及保存 {% data variables.large_files.product_name_short %} 下载的位置。

 {% endnote %}
4. 要安装该文件，请运行以下命令：
  ```shell
  $ ./install.sh
  > {% data variables.large_files.product_name_short %} initialized.
  ```
 {% note %}

 **注意：** 你可能必须使用 `sudo ./install.sh` 来安装该文件。

 {% endnote %}
5. 验证安装成功：
  ```shell
  $ git {% data variables.large_files.command_name %} install
  > {% data variables.large_files.product_name_short %} initialized.
  ```
6. 如果未显示表示 `git {% data variables.large_files.command_name %} install` 成功的消息，请联系 {% data variables.contact.contact_support %}。 确保包含操作系统的名称。

{% endmac %}

{% windows %}

1. 导航到 [git-lfs.github.com](https://git-lfs.github.com) 并单击“下载”。

  {% tip %}

  **提示：** 要详细了解为 Windows 安装 {% data variables.large_files.product_name_short %} 的可选方法，请参阅此 [入门指南](https://github.com/github/git-lfs#getting-started)。

  {% endtip %}
2. 在计算机上，找到下载的文件。
3. 双击文件 git-lfs-windows-1.X.X.exe，其中 1.X.X 替换为你下载的 Git LFS 版本。 打开此文件时，Windows 将运行安装程序向导以安装 {% data variables.large_files.product_name_short %}。
{% data reusables.command_line.open_the_multi_os_terminal %}
5. 验证安装成功：
  ```shell
  $ git {% data variables.large_files.command_name %} install
  > {% data variables.large_files.product_name_short %} initialized.
  ```
6. 如果未显示表示 `git {% data variables.large_files.command_name %} install` 成功的消息，请联系 {% data variables.contact.contact_support %}。 确保包含操作系统的名称。

{% endwindows %}

{% linux %}

1. 导航到 [git-lfs.github.com](https://git-lfs.github.com) 并单击“下载”。

  {% tip %}

  **提示：** 要详细了解为 Linux 安装 {% data variables.large_files.product_name_short %} 的可选方法，请参阅此 [入门指南](https://github.com/github/git-lfs#getting-started)。

  {% endtip %}
2. 在计算机上，找到并解压缩下载的文件。
{% data reusables.command_line.open_the_multi_os_terminal %}
3. 将当前工作目录更改为您下载并解压缩的文件夹。
  ```shell
  $ cd ~/Downloads/git-lfs-<em>1.X.X</em>
  ```
 {% note %}

 **注意：** 在 `cd` 后面使用的文件路径取决于你的操作系统、下载的 Git LFS 版本以及保存 {% data variables.large_files.product_name_short %} 下载的位置。

 {% endnote %}
4. 要安装该文件，请运行以下命令：
  ```shell
  $ ./install.sh
  > {% data variables.large_files.product_name_short %} initialized.
  ```
 {% note %}

 **注意：** 你可能必须使用 `sudo ./install.sh` 来安装该文件。

 {% endnote %}
5. 验证安装成功：
  ```shell
  $ git {% data variables.large_files.command_name %} install
  > {% data variables.large_files.product_name_short %} initialized.
  ```
6. 如果未显示表示 `git {% data variables.large_files.command_name %} install` 成功的消息，请联系 {% data variables.contact.contact_support %}。 确保包含操作系统的名称。

{% endlinux %}

## 延伸阅读

- [配置 {% data variables.large_files.product_name_long %}](/articles/configuring-git-large-file-storage)
