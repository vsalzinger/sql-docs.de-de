---
title: Sys. fulltext_semantic_languages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5c112a48acfa87adcdee439cea320c44a604bfe2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="sysfulltextsemanticlanguages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Sprache zurück, deren Statistikmodell für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert ist. Wenn ein Sprachenmodell registriert ist, wird diese Sprache für die semantische Indizierung aktiviert.  
  
 Diese Katalogsicht ähnelt [Sys. fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
    
||||  
|-|-|-|  
|**Spaltenname**|**Typ**|**Beschreibung**|  
|lcid|int|Microsoft Windows-Gebietsschemabezeichner (Locale Identifier, LCID) für die Sprache.|  
|name|sysname|Der Wert des Alias in [sys.syslanguages &#40;Transact-SQL&#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) entsprechend dem Wert der **Lcid**, oder die Zeichenfolgendarstellung des numerischen LCID-WERTS.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie unter [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Für Weitere Informationen zu der semantischen sprachstatistikdatenbank, die zur Unterstützung der semantischen Indizierung installiert ist, Fragen Sie die Katalogsicht [Sys. fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Die Sichtbarkeit der Metadaten in Katalogsichten ist auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt wie Abfrage **fulltext_semantic_languages** zum Abrufen von Informationen zu allen sprachenmodellen registriert wird, für die semantische Indizierung auf die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
