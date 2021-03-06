---
title: "Cl.exe 的返回值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85ca64178a4914cfbbc8b3a717b87ab5590cd778
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="return-value-of-clexe"></a>cl.exe 的返回值
cl.exe 在成功（无错误）时返回零；否则返回非零值。  
  
 如果从脚本、powershell、.cmd 或 .bat 文件编译，则 cl.exe 的返回值很有用。 建议在出现错误或警告时捕获编译器的输出，以便能解决它们。  
  
 有太多可能的错误退出代码，cl.exe 无法将它们一一列出。 你可以查找错误代码在 winerror.h 或 ntstatus.h 文件包括在 Windows 软件开发工具包中的 %programfiles (x86) %\Windows 工具包\\`version`\Include\shared\ directory。 以十进制返回的错误代码必须转换为十六进制才能搜索。 例如，错误代码 -1073741620 转换为十六进制为 0xC00000CC。 在 ntstatus.h 中发现了此错误，对应的消息为“无法在远程服务器上找到指定共享名。” 有关可下载的 Windows 错误代码列表，请参阅[&#91;MS ERREF &#93;: Windows 错误代码](http://msdn.microsoft.com/library/cc231196)。  
  
 还可使用 Visual Studio 中的错误查找实用工具来了解编译器错误消息的意思。 在 Visual Studio 命令外壳中，输入**errlook.exe**以启动此实用工具; 或者在 Visual Studio IDE 中，在菜单栏上，选择**工具**，**错误查找**。 输入错误值以查找与错误相关的描述性文本。 有关详细信息请参阅[ERRLOOK 参考](../../build/reference/errlook-reference.md)。  
  
## <a name="remarks"></a>备注  
 下面是一个使用 cl.exe 的返回值的示例 .bat 文件。  
  
```  
echo off  
cl /W4 t.cpp  
@if ERRORLEVEL == 0 (  
   goto good  
)  
  
@if ERRORLEVEL != 0 (  
   goto bad  
)  
  
:good  
   echo "clean compile"  
   echo %ERRORLEVEL%  
   goto end  
  
:bad  
   echo "error or warning"  
   echo %ERRORLEVEL%  
   goto end  
  
:end  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)