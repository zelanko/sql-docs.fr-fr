---
title: Types de données et comportement de chargement en masse XML (SQLXML)
description: En savoir plus sur les types de données et le comportement de chargement en masse XML dans SQLXML 4,0.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3cbf84c0f5bf4f80bc3bf12d6dad91479888d595
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97462900"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Types de données et comportement du chargement en masse XML (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Les types de données spécifiés dans le schéma de mappage (type XSD ou XDR et **SQL : DataType**) sont généralement ignorés, sauf dans les cas suivants :  
  
 Dans XSD :  
  
-   Si le type est **DateTime** ou **Time**, vous devez spécifier **SQL : DataType** car le chargement en masse XML effectue une conversion de données avant d’envoyer les données à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Lorsque vous effectuez un chargement en masse dans une colonne de type **uniqueidentifier** dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et que la valeur xsd est un GUID qui comprend des accolades ({et}), vous devez spécifier **SQL : datatype = "uniqueidentifier"** pour supprimer les accolades avant que la valeur ne soit insérée dans la colonne. Si **SQL : DataType** n’est pas spécifié, la valeur est envoyée avec les accolades et l’insertion échoue.  
  
 Pour plus d’informations sur **SQL : DataType**, consultez [forçages de type de données et l’annotation sql : datatype &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Dans XDR :  
  
-   Si **DT : type** est **DateTime**, **Time**, **DateTime.tz** ou **Time.tz**, vous devez spécifier les types de données **DT : type** et **SQL : DataType** car le chargement en masse XML effectue une conversion de données avant d’envoyer les données à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Si vos données XML sont de type **UUID**, **SQL : DataType** doit être spécifié ; **DT : type = "UUID"** est également requis, sauf si les données sont des données de chaîne. Si vous ne spécifiez pas **DT : UUID**, le chargement en masse XML accepte des chaînes avec des accolades (et les supprime si nécessaire).  
  
-   Si les données XML sont **bin. base64** ou **bin. hex**, vous devez spécifier le type de données XML avec **DT : type**. Le chargement en masse XML charge ensuite les données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous la forme d'une représentation hexadécimale des données.  
  
  
