---
title: "使用 lastprivate 子句 A.6 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1744787e1dfb90fa9af93db5dba4eecd600b4334
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   使用 lastprivate 子句
有时正确的执行取决于循环的最后一个迭代分配给变量的值。 此类程序都必须列出所有此类变量作为自变量到`lastprivate`子句 ([部分 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md)第 27 页上)，以便变量的值与按顺序执行循环时相同。  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 在前面的示例中，值`i`并行区域末尾将等于`n-1`，如下所示的顺序的情况。