---
title: "_CrtMemDumpAllObjectsSince | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDumpAllObjectsSince
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1c04d21b1c4009bd93e608d1c243d5b459e2422
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2018
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince
从程序开始执行或从指定的堆状态转储堆中对象的信息（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>参数  
 `state`  
 指向开始从其转储的堆状态的指针，或 **NULL**。  
  
## <a name="remarks"></a>备注  
 `_CrtMemDumpAllObjectsSince` 函数以用户可读的形式转储堆中分配的对象的调试标头信息。 应用程序可以使用转储信息来跟踪分配并检测内存问题。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtMemDumpAllObjectsSince` 的调用。  
  
 `_CrtMemDumpAllObjectsSince` 使用 `state` 参数的值确定启动转储操作的位置。 要从指定堆状态开始转储，`state` 参数必须是指向 **_CrtMemState** 结构的指针，此结构在调用 `_CrtMemDumpAllObjectsSince` 前已由 [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 填充。 当 `state` 为 **NULL** 时，该函数从程序开始执行时即开始转储。  
  
 如果应用程序通过调用 [_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md) 安装了转储挂钩函数，那么每次 `_CrtMemDumpAllObjectsSince` 转储有关 `_CLIENT_BLOCK` 块类型的信息时，它都会调用应用程序提供的转储函数。 默认情况下，内存转储操作不包含内部 C 运行时块 (`_CRT_BLOCK`)。 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数可用于打开 **_crtDbgFlag** 的 `_CRTDBG_CHECK_CRT_DF` 位，以将这些块包括在内。 此外，标记为已释放或已忽略的块（**_FREE_BLOCK**、**_IGNORE_BLOCK**）不包括在内存转储中。  
  
 有关堆状态函数和 `_CrtMemState` 结构的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="example"></a>示例  
 有关如何使用 `_CrtMemDumpAllObjectsSince` 的示例，请参阅 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。  
  
## <a name="see-also"></a>请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)