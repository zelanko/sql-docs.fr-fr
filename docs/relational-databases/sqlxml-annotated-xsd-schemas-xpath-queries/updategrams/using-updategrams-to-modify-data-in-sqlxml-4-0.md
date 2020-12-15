---
title: Utilisation de codes de mise à jour (updategrams) pour modifier des données dans SQLXML 4.0
description: Affichez des informations et des exemples sur codes et la façon dont ils sont utilisés pour modifier les données dans SQLXML 4,0.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ccbc5c7027fcf6c5b867f842f77bd4c1ec99dd2a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97439590"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a>Utilisation de codes de mise à jour (updategrams) pour modifier des données dans SQLXML 4.0
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Vous pouvez modifier (insérer, mettre à jour ou supprimer) une base de données dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir d’un document XML existant à l’aide d’un mise à jour ou de la [!INCLUDE[tsql](../../../includes/tsql-md.md)] fonction OpenXml.  
  
 Cette section fournit des informations sur les codes de mise à jour (updategrams) et propose des exemples pour leur utilisation.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation de codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/introduction-to-updategrams-sqlxml-4-0.md)  
 Fournit des informations de base et des exemples de codes de mise à jour (updategrams).  
  
 [Spécification d’un schéma de mappage annoté dans un mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 Décrit et fournit des exemples de schémas de mappage annotés dans les codes de mise à jour (updategrams).  
  
 [Gestion des valeurs NULL &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/null-handling-sqlxml-4-0.md)  
 Décrit comment spécifier la valeur NULL pour des valeurs d'élément et d'attribut.  
  
 [Insertion de données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples d'utilisation de codes de mise à jour (updategrams) pour insérer des données.  
  
 [Suppression de données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples d'utilisation de codes de mise à jour (updategrams) pour supprimer des données.  
  
 [Mise à jour des données à l’aide de codes XML &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples d'utilisation de codes de mise à jour (updategrams) pour modifier des données existantes.  
  
 [Passage de paramètres à codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples de transmission de paramètres aux codes de mise à jour (updategrams).  
  
 [Gestion des problèmes d’accès concurrentiel de la base de données dans codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 Décrit les divers niveaux de protection possibles pour gérer des problèmes d'accès concurrentiel dans les codes de mise à jour (updategrams) et fournit des exemples.  
  
 [Exemples d’applications mise à jour &#40;SQLXML 4,0&#41;]()  
 Fournit des exemples d'applications qui utilisent des codes de mise à jour (updategrams).  
  
 [Instructions et limitations de XML codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 Répertorie certains éléments à retenir lors de l'utilisation de codes de mise à jour (updategrams).  
  
