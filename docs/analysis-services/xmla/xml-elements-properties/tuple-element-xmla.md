---
title: Tuple-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9f7f7d21f64c502e60ee0f6c95d2b6cbfd09c1b7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="tuple-element-xmla"></a>Tuple-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Sammlung von [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)-Elementen, die im übergeordneten [Tuples](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)-Element enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Tupel](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
|Untergeordnete Elemente|[Datenmember](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Clientanwendung die **AxisFormat**-Eigenschaft auf *TupleFormat* festlegt, wird eine Achse als Menge von Tupeln dargestellt. Jedes **Axis**-Element enthält ein **Tuples**-Element, das die Menge von Tupeln auf dieser Achse darstellt. Jedes Tupel wird mithilfe eines **Tuple**-Elements dargestellt, das **Member**-Elemente aus jeder Hierarchie auf der Achse enthält.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Struktur des **Tuple**-Elements, wenn ein Client *TupleFormat* oder *CustomFormat* für die XMLA-Eigenschaft **AxisFormat** festlegt, wobei die folgenden Elemente für die Achse vorhanden sind:  
  
|||||  
|-|-|-|-|  
|**Time**-Hierarchie|1999|1999|2000|  
|**Category**-Hierarchie|Tatsächlich|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
