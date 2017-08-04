---
title: Codieren eines benutzerdefinierten ForEach-Enumerators | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom foreach enumerators [Integration Services], coding
ms.assetid: 279cf6de-d06f-40e7-b8ca-569310449f36
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 74e6e838c3dcfb18e52a8fbf460a5b71ee25399a
ms.contentlocale: de-de
ms.lasthandoff: 08/03/2017

---
# <a name="coding-a-custom-foreach-enumerator"></a>Codieren eines benutzerdefinierten Foreach-Enumerators
  Nachdem Sie eine Klasse erstellt haben, die von der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>-Basisklasse erbt, und das <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>-Attribut auf die Klasse angewendet haben, müssen Sie die Implementierung der Eigenschaften und Methoden der Basisklasse überschreiben, um die benutzerdefinierte Funktionalität bereitzustellen.  
  
 Ein funktionstüchtiges Beispiel eines benutzerdefinierten Enumerators finden Sie unter [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten foreach-Enumerator](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-user-interface-for-a-custom-foreach-enumerator.md).  
  
## <a name="initializing-the-enumerator"></a>Initialisieren des Enumerators  
 Sie können die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A>-Methode verwenden, um Verweise auf die im Paket definierten Verbindungs-Manager zwischenzuspeichern und um Verweise auf die Ereignisschnittstelle zwischenzuspeichern, die Sie verwenden können, um Fehler, Warnungen und Informationsmeldungen auszulösen.  
  
## <a name="validating-the-enumerator"></a>Überprüfen des Enumerators  
 Überschreiben Sie die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A>-Methode, um zu überprüfen, ob der Enumerator ordnungsgemäß konfiguriert ist. Wenn die-Methode zurückgibt **Fehler**, der Enumerator und das Paket, das den Enumerator enthält nicht ausgeführt werden. Die Implementierung dieser Methode ist für jeden Enumerator spezifisch. Wenn jedoch der Enumerator auf <xref:Microsoft.SqlServer.Dts.Runtime.Variable>- oder <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>-Objekten basiert, sollten Sie Code hinzufügen, um zu überprüfen, ob diese Objekte in den Auflistungen, die der Methode bereitgestellt werden, vorhanden sind.  
  
 Im folgenden Codebeispiel wird die Implementierung von <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> gezeigt, die nach einer in einer Eigenschaft des Enumerators angegebenen Variablen sucht.  
  
```csharp  
private string variableNameValue;  
  
public string VariableName  
{  
    get{ return this.variableNameValue; }  
    set{ this.variableNameValue = value; }  
}  
  
public override DTSExecResult Validate(Connections connections, VariableDispenser variableDispenser, IDTSInfoEvents infoEvents, IDTSLogging log)  
{  
    if (!variableDispenser.Contains(this.variableNameValue))  
    {  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + this.variableNameValue + " does not exist in the collection.", "", 0);  
            return DTSExecResult.Failure;  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Private variableNameValue As String  
  
Public Property VariableName() As String  
    Get   
         Return Me.variableNameValue  
    End Get  
    Set (ByVal Value As String)   
         Me.variableNameValue = value  
    End Set  
End Property  
  
Public Overrides Function Validate(ByVal connections As Connections, ByVal variableDispenser As VariableDispenser, ByVal infoEvents As IDTSInfoEvents, ByVal log As IDTSLogging) As DTSExecResult  
    If Not variableDispenser.Contains(Me.variableNameValue) Then  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + Me.variableNameValue + " does not exist in the collection.", "", 0)  
            Return DTSExecResult.Failure  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
## <a name="returning-the-collection"></a>Zurückgeben der Auflistung  
 Während der Ausführung ruft der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>-Container die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>-Methode des benutzerdefinierten Enumerators auf. In dieser Methode erstellt der Enumerator seine Auflistung von Elementen und füllt sie auf und gibt dann die Auflistung zurück. <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> führt dann eine Iteration für die Elemente in der Auflistung durch und führt die Ablaufsteuerung für jedes Element in der Auflistung durch.  
  
 Im folgenden Beispiel wird eine Implementierung von <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> gezeigt, wobei ein Array zufälliger ganzer Zahlen zurückgegeben wird.  
  
```csharp  
public override object GetEnumerator()  
{  
    ArrayList numbers = new ArrayList();  
  
    Random randomNumber = new Random(DateTime.Now);  
  
    for( int x=0; x < 100; x++ )  
        numbers.Add( randomNumber.Next());  
  
    return numbers;  
}  
```  
  
```vb  
Public Overrides Function GetEnumerator() As Object  
    Dim numbers As ArrayList =  New ArrayList()   
  
    Dim randomNumber As Random =  New Random(DateTime.Now)   
  
        Dim x As Integer  
        For  x = 0 To  100- 1  Step  x + 1  
        numbers.Add(randomNumber.Next())  
        Next  
  
    Return numbers  
End Function  
```  
 
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten ForEach-Enumerators](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)   
 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten foreach-Enumerator](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  