---
title: XML et les Types de données en bloc le comportement de chargement (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 95fdeec756a149f0663bfb337eb2103085fb8859
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52807411"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Types de données et comportement du chargement en masse XML (SQLXML 4.0)
  Les types de données spécifiés dans le schéma de mappage (type XSD ou XDR et `sql:datatype`) sont ignorés en général, sauf dans les cas suivants :  
  
 Dans XSD :  
  
-   Si le type est `dateTime` ou `time`, vous devez spécifier `sql:datatype` car le chargement en masse XML effectue une conversion de données avant d'envoyer les données à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Lorsque vous effectuez un chargement en bloc dans une colonne de `uniqueidentifier` tapez [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et la valeur XSD est un GUID qui inclut des accolades ({et}), vous devez spécifier **SQL : DataType = « uniqueidentifier »** pour supprimer les accolades avant que la valeur est inséré dans la colonne. Si `sql:datatype` n'est pas spécifié, la valeur est envoyée avec les accolades et l'insertion échoue.  
  
 Pour plus d’informations sur `sql:datatype`, consultez [forçages de Type de données et de l’Annotation SQL : DataType &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Dans XDR :  
  
-   Si `dt:type` est `datetime`, `time`, `dateTime.tz` ou `time.tz`, vous devez spécifier les types de données `dt:type` et `sql:datatype` car le chargement en masse XML effectue une conversion de données avant d'envoyer les données à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Si vos données XML sont de type `uuid`, `sql:datatype` doit être spécifié ; **dt : type = « uuid »** est également requis, sauf si les données sont des données de type chaîne. Si vous ne spécifiez pas `dt:uuid`, le chargement en masse XML accepte les chaînes avec accolades (et les supprime si nécessaire).  
  
-   Si les données XML sont `bin.base64` ou `bin.hex`, vous devez spécifier le type de données XML avec `dt:type`. Le chargement en masse XML charge ensuite les données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous la forme d'une représentation hexadécimale des données.  
  
  
