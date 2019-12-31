---
title: Considérations sur la sécurité des schémas annotés (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
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
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 87af92866658e2fa5b4f8648e2a22dbf3d1cb13f
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75252510"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>Considérations sur la sécurité des schémas annotés (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les éléments suivants constituent les indications de sécurité relatives à l'utilisation des schémas annotés :  
  
-   Évitez d'utiliser le mappage par défaut dans les schémas de mappage. Le mappage par défaut expose les informations sur la base de données (noms de table et noms de colonne) dans le document XML obtenu parce que, par défaut, les noms d'élément sont mappés avec les noms de table et les noms d'attribut avec les noms de colonne. Par conséquent, tout utilisateur qui consulte le document XML a accès aux informations sur les tables et les colonnes de la base de données, d'où un problème de sécurité potentiel. Pour éviter ce risque, spécifiez des noms d'élément et d'attribut arbitraires dans le schéma et utilisez les annotations pour les mapper explicitement avec les tables et les colonnes. Pour plus d’informations sur l’utilisation du mappage par défaut lorsque vous créez des schémas XSD, consultez [mappage par défaut d’éléments et d’attributs XSD à des tables et des colonnes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   Le mappage explicite spécifié à l'aide d'annotations expose les informations sur la base de données (telles que les noms de table et les noms de colonne). Par conséquent, il se peut que vous ne souhaitiez pas rendre ces schémas disponibles publiquement.  
  
-   Certaines requêtes, telles que celles qui sont spécifiées par rapport à un schéma de mappage avec récurrence (spécifiée à l’aide d’une annotation **max-depth** définie sur une valeur supérieure) peuvent prendre plus de temps à s’exécuter. Vous pouvez éventuellement spécifier une limite de délai d’attente en définissant la propriété délai d’expiration de la commande (en secondes). Par exemple :  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Schémas XSD annotés dans SQLXML 4.0](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
