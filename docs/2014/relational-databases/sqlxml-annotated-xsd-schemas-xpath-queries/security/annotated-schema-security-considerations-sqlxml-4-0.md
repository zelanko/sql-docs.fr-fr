---
title: Annoté considérations de sécurité de schéma (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b46c996c7b89be06558d3ad4b43e1c1bca6aa370
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162321"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>Considérations sur la sécurité des schémas annotés (SQLXML 4.0)
  Les éléments suivants constituent les indications de sécurité relatives à l'utilisation des schémas annotés :  
  
-   Évitez d'utiliser le mappage par défaut dans les schémas de mappage. Le mappage par défaut expose les informations sur la base de données (noms de table et noms de colonne) dans le document XML obtenu parce que, par défaut, les noms d'élément sont mappés avec les noms de table et les noms d'attribut avec les noms de colonne. Par conséquent, tout utilisateur qui consulte le document XML a accès aux informations sur les tables et les colonnes de la base de données, d'où un problème de sécurité potentiel. Pour éviter ce risque, spécifiez des noms d'élément et d'attribut arbitraires dans le schéma et utilisez les annotations pour les mapper explicitement avec les tables et les colonnes. Pour plus d’informations sur l’utilisation de mappage par défaut lorsque vous créez des schémas XSD, consultez [mappage par défaut d’éléments XSD et des attributs aux Tables et colonnes &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   Le mappage explicite spécifié à l'aide d'annotations expose les informations sur la base de données (telles que les noms de table et les noms de colonne). Par conséquent, il se peut que vous ne souhaitiez pas rendre ces schémas disponibles publiquement.  
  
-   Certaines requêtes telles que celles spécifiées sur le schéma de mappage avec récurrence (spécifiée à l'aide de l'annotation `max-depth` définie avec une valeur supérieure) peuvent nécessiter plus de temps pour s'exécuter. Vous pouvez éventuellement spécifier une limite de délai d’attente en définissant la propriété de commande, délai d’expiration (en secondes). Exemple :  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Schémas XSD annotés dans SQLXML 4.0](../../sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
