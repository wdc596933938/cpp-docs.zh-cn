---
title: "编译器警告 （等级 3） C4373 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4373
dev_langs: C++
helpviewer_keywords: C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43523cb5f4c024ec3e937e88fca7f78c341ab19d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4373"></a>编译器警告（等级 3）C4373
“%$S”: 虚函数重写“%$pS”，当参数只在 const/volatile 限定符上有差异时，早期版本的编译器未进行重写  
  
 应用程序在派生类中包含一个方法，可重写基类中的虚拟方法，在重写方法中的参数中，只有 [const](../../cpp/const-cpp.md) 或 [volatile](../../cpp/volatile-cpp.md) 限定符与虚拟方法中的参数不同。 这就意味着编译器必须将函数引用绑定到基类或派生类中的方法。  
  
 [!INCLUDE[cpp_orcas_long](../../cpp/includes/cpp_orcas_long_md.md)] 之前版本的编译器将函数绑定到基类中的方法，然后发出一条警告消息。 后续版本的编译器忽略 `const` 或 `volatile` 限定符，将函数绑定到派生类中的方法，然后发出警告 `C4373`。 后一种行为符合 C++ 标准。  
  
## <a name="example"></a>示例  
 下面的代码示例将生成警告 C4373。  
  
```  
// c4373.cpp  
// compile with: /c /W3  
#include <stdio.h>  
struct Base  
{  
    virtual void f(int i) {  
        printf("base\n");  
    }  
};  
struct Derived : Base  
{  
    void f(const int i) {  // C4373  
        printf("derived\n");  
    }  
};  
void main()  
{  
    Derived d;  
    Base* p = &d;  
    p->f(1);  
}  
```  
  
```Output  
derived  
```