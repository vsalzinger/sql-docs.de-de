---
title: Sp_rxPredict | Microsoft Docs
ms.custom: 
ms.date: 07/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_rxPredict procedure
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c150649eb7cc45de0d3587a006a58af9bb416b4c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Generiert einen vorhergesagten Wert auf Grundlage eines gespeicherten Modells.

Stellt die Bewertung auf Machine Learning-Modellen in nahezu in Echtzeit. `sp_rxPredict`ist eine gespeicherte Prozedur bereitgestellt, die als Wrapper für die `rxPredict` -Funktion in ["revoscaler"](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) und [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package). Es ist in C++ geschrieben wurde und ist speziell für die Bewertung Vorgänge optimiert. Es unterstützt sowohl R oder Python machine Learning-Modellen.

**Dieses Thema gilt für**:  
- SQL Server 2017  
- SQL Server 2016-R-Services mit dem Upgrade auf Microsoft R Server  

## <a name="syntax"></a>Syntax

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Argumente

**model**

Ein vortrainierte Modell in einem unterstützten Format. 

**Eingabe**

Eine gültige SQL-Abfrage

### <a name="return-values"></a>Rückgabewerte

Eine Spalte Faktor ist sowie alle Pass-Through-Spalten aus der Eingabedatenquelle zurückgegeben.
Zusätzliche Spalten, z. B. Konfidenzintervall bewerten, zurückgegeben werden kann, wenn der Algorithmus unterstützt die Erstellung solcher Werte.

## <a name="remarks"></a>Hinweise

Um die gespeicherte Prozedur verwendet werden kann, muss die SQLCLR für die Instanz aktiviert sein.

> [!NOTE]
> Beachten Sie die Sicherheitsrisiken, bevor Sie diese Option aktivieren.

Der Benutzer muss `EXECUTE` Berechtigung für die Datenbank.

### <a name="supported-platforms"></a>Unterstützte Plattformen

Erfordert eine der folgenden Editionen:  
- SQL Server 2017 Machine Learning Services (einschließlich Microsoft R Server 9.1.0)  
- Microsoft Machine Learning-Server  
- SQL Server R Services 2016 mit einer Aktualisierung der R-Services-Instanz für Microsoft R Server 9.1.0 oder höher  

### <a name="supported-algorithms"></a>Algorithmen unterstützt:

Eine Liste der unterstützten Algorithmen, finden Sie unter [Echtzeit Bewertung](../../advanced-analytics/real-time-scoring.md).

Die folgenden Modelltypen sind **nicht** unterstützt:  
- Modelle, die mit anderen, nicht unterstützte Arten von R-Transformationen  
- Modelle mit der `rxGlm` oder `rxNaiveBayes` Algorithmen in "revoscaler"  
- PMML-Modelle  
- Mit anderen R-Bibliotheken von CRAN oder anderen Repositorys erstellte Modelle  
- Modelle, die eine beliebige andere Art von R-Transformation, andere als die hier aufgeführten enthält  

## <a name="examples"></a>Beispiele

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Abgesehen davon, dass eine gültige SQL-Abfrage, die Eingabedaten in  *@inputData*  Spalten, die kompatibel mit den Spalten im Modell gespeicherten enthalten.

`sp_rxPredict`unterstützt nur die folgenden .NET Spaltentypen: double, Float, Short, Ushort, long, ulong-Typ und Zeichenfolge. Sie müssen möglicherweise den nicht unterstützten Typen der Eingabedaten herausfiltern, bevor Sie sie für die Bewertung in Echtzeit zu verwenden. 

  Informationen zur entsprechenden SQL-Datentypen finden Sie unter [SQL-CLR-Typzuordnung](https://msdn.microsoft.com/library/bb386947.aspx) oder [Zuordnen von CLR-Parameterdaten](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).
