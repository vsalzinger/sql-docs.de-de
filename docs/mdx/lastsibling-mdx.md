---
title: LastSibling (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LASTSIBLING
dev_langs:
- kbMDX
helpviewer_keywords:
- LastSibling function
ms.assetid: 05542812-4bdb-48bf-823e-065d105b1721
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: aff9f57812d1f7af2f94c090655cc806133e815d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="lastsibling-mdx"></a>LastSibling (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt das letzte untergeordnete Element des übergeordneten Elements eines angegebenen Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.LastSibling   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Standardmeasure für den letzten Tag im Juli 2002 zurückgegeben.  
  
```  
SELECT [Date].[Fiscal].[Date].&[20020717].LastSibling   
   ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
