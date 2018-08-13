---
title: Pour modifier des données dans SQLXML 4.0 à l’aide de codes | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
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
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 7a6e29fdb90e0e0eee35d6b072e25b1ffc6451e1
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39545549"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a>Utilisation de codes de mise à jour (updategrams) pour modifier des données dans SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Vous pouvez modifier (insérer, mettre à jour ou supprimer) une base de données [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir d’un XML existant de document à l’aide d’une mise à jour ou OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] (fonction).  
  
 Cette section fournit des informations sur les codes de mise à jour (updategrams) et propose des exemples pour leur utilisation.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation des codes de mise à &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/introduction-to-updategrams-sqlxml-4-0.md)  
 Fournit des informations de base et des exemples de codes de mise à jour (updategrams).  
  
 [Spécification d’un schéma de mappage annoté dans une mise à jour &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 Décrit et fournit des exemples de schémas de mappage annotés dans les codes de mise à jour (updategrams).  
  
 [Gestion des valeurs NULL &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/null-handling-sqlxml-4-0.md)  
 Décrit comment spécifier la valeur NULL pour des valeurs d'élément et d'attribut.  
  
 [Insertion de données à l’aide de codes XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples d'utilisation de codes de mise à jour (updategrams) pour insérer des données.  
  
 [Suppression des données à l’aide de codes XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples d'utilisation de codes de mise à jour (updategrams) pour supprimer des données.  
  
 [La mise à jour des données à l’aide de codes XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples d'utilisation de codes de mise à jour (updategrams) pour modifier des données existantes.  
  
 [Passage de paramètres aux codes &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md)  
 Décrit et fournit des exemples de transmission de paramètres aux codes de mise à jour (updategrams).  
  
 [Gestion des problèmes de concurrence de base de données dans les codes &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 Décrit les divers niveaux de protection possibles pour gérer des problèmes d'accès concurrentiel dans les codes de mise à jour (updategrams) et fournit des exemples.  
  
 [Exemples de mise à jour d’Applications &#40;SQLXML 4.0&#41;](http://msdn.microsoft.com/library/d2287e10-4007-4ba4-ad84-4e2b6adfede5)  
 Fournit des exemples d'applications qui utilisent des codes de mise à jour (updategrams).  
  
 [Règles et Limitations des codes XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 Répertorie certains éléments à retenir lors de l'utilisation de codes de mise à jour (updategrams).  
  
  
