---
title: 下載並安裝 sqlpackage |Microsoft Docs
description: 下載並安裝適用於 Windows、 macOS 或 Linux 的 sqlpackage
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: ecefe3f1abe47a1a4f1af967cb1a15ee9f4dd52b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800256"
---
# <a name="download-and-install-sqlpackage"></a>下載並安裝 sqlpackage

Windows、 macOS 和 Linux 上，執行 sqlpackage。

下載並安裝最新的.NET Framework 版本和 macOS 及 Linux 預覽：

|平台|下載|發行日期|Version|建置|
|:---|:---|:---|:---|:---|
|Windows|[安裝程式](https://go.microsoft.com/fwlink/?linkid=875508)|2018 年 6 月 20 日|17.8|14.0.4079.2|
|macOS (預覽)|[.zip](https://go.microsoft.com/fwlink/?linkid=873927)|2018 年 5 月 9 日 |0.0.1|15.0.4057.1|
|Linux (預覽)|[.zip](https://go.microsoft.com/fwlink/?linkid=873926)|2018 年 5 月 9 日 |0.0.1|15.0.4057.1|

如需最新版本的詳細資訊，請參閱[版本資訊](sqlpackage-release-notes.md)。

## <a name="get-sqlpackage-for-windows"></a>取得 Windows sqlpackage

這個版本的 sqlpackage 包括標準的 Windows 安裝程式體驗，以及用.zip 格式： 

1. 下載並執行[DacFramework.msi installer Windows](https://go.microsoft.com/fwlink/?linkid=875508)。
2. 開啟新的 [命令提示字元] 視窗，然後執行 sqlpackage.exe
    - sqlpackage 會安裝到```C:\Program Files\Microsoft SQL Server\140\DAC\bin```資料夾

## <a name="get-sqlpackage-preview-for-macos"></a>取得適用於 macOS 的 sqlpackage （預覽）

1. 下載[適用於 macOS 的 sqlpackage](https://go.microsoft.com/fwlink/?linkid=873927)。
2. 若要將檔案解壓縮，並啟動 sqlpackage，開啟新的終端機視窗並輸入下列命令：

   **.zip 安裝：**

   ```bash
   mv ~/Downloads/sqlpackage-linux-<version string> ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>取得適用於 Linux 的 sqlpackage （預覽）

1. 下載[適用於 Linux 的 sqlpackage](https://go.microsoft.com/fwlink/?linkid=873926)使用其中一種安裝程式或.tar.gz 下載封存：
2. 若要將檔案解壓縮，並啟動 sqlpackage，開啟新的終端機視窗並輸入下列命令：

   **.zip 安裝：**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bashrc
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > 在 Debian、 Redhat 和 Ubuntu 上，您可能有遺失相依性。 若要安裝這些相依性，視您的 Linux 版本而定，使用下列命令：

   **Debian:**

   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat:**

   ```bash
   yum install libunwind
   yum install libicu
   ```

   **Ubuntu:**

   ```bash
   sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   sudo apt-get install libicu52      # for 14.x
   sudo apt-get install libicu55      # for 16.x
   sudo apt-get install libicu57      # for 17.x
   sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>解除安裝 sqlpackage （預覽）

如果您安裝使用 Windows installer 的 sqlpackage，然後解除安裝您移除任何 Windows 應用程式的方式相同。

如果您使用.zip 或其他封存安裝 sqlpackage，只要刪除檔案。

## <a name="supported-operating-systems"></a>支援的作業系統

sqlpackage Windows、 macOS 和 Linux 上執行，並支援下列平台：

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- 深入了解[sqlpackage](sqlpackage.md)

[Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
