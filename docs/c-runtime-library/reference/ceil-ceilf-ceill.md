---
title: "ceil、ceilf、ceill | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs: C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4831b9f6f046dbc1a5d337f22e6be3dc3f4a5662
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ceil-ceilf-ceill"></a>ceil、ceilf、ceill
计算一个值的上限。  
  
## <a name="syntax"></a>语法  
  
```  
double ceil(   
   double x   
);  
float ceil(  
   float x  
);  // C++ only  
long double ceil(  
   long double x  
);  // C++ only  
float ceilf(  
   float x  
);  
long double ceill(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 浮点值。  
  
## <a name="return-value"></a>返回值  
 `ceil` 函数将返回表示大于或等于 `x` 的最小整数的浮点值。 无错误返回。  
  
|输入|SEH 异常|Matherr 异常|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|无|`_DOMAIN`|  
  
 `ceil` 具有使用流式处理 SIMD 扩展 2 (SSE2) 的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此你可以调用 `ceil` 的重载。 在 C 程序中，`ceil` 始终采用及返回双精度型。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`ceil`, `ceilf`, `ceill`|\<math.h>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [floor](../../c-runtime-library/reference/floor-floorf-floorl.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)
