---
title: À l’aide du fournisseur SQLXMLOLEDB (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aa47713fd51de86b2ed547f094ec407e1d7caae9
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67584865"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>Utilisation du fournisseur SQLXMLOLEDB (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les rubriques de cette section présentent des exemples d'application ADO qui illustrent l'utilisation des propriétés spécifiques au fournisseur SQLXMLOLEDB.  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>Spécifications de l'application pour le fournisseur SQLXMLOLEDB 4.0  
 Pour créer des exemples fonctionnels qui utilisent SQLXMLOLEDB 4.0, vous devez effectuer les opérations suivantes :  
  
1.  Créer une application Microsoft Visual Basic.exe et ajouter l'une des références suivantes :  
  
    -   Microsoft ActiveX Data Objects 2.6 bibliothèque  
  
    -   Microsoft ActiveX Data Objects 2.7 Library  
  
    -   Bibliothèque Microsoft ADO 2.8  
  
2.  Déployer et installer SQLXML 4.0 et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     For more information, see on [SQLXML 4.0 Programming Concepts](../../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md) and [Installing SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exécution de requêtes SQL &#40;fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md)  
 Illustre l’utilisation des propriétés racine ClientSideXML et xml pour exécuter des requêtes SQL.  
  
 [Exécution de modèles qui contiennent des requêtes SQL &#40;fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 Illustre l’utilisation de la propriété ClientSideXML.  
  
 [Exécution de requêtes XPath &#40;fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md)  
 Illustre l’utilisation des propriétés ClientSideXML, chemin d’accès de Base et schéma de mappage.  
  
 [L’exécution de requêtes XPath avec des espaces de noms &#40;fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 Illustre la procédure d'interrogation sur des schémas qualifiés par un espace de noms.  
  
 [Exécution de modèles qui contiennent des requêtes XPath &#40;fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 Montre comment exécuter des modèles avec des requêtes SQL en utilisant les propriétés ClientSideXML, chemin d’accès de Base et schéma de mappage.  
  
 [Appliquer une Transformation XSL &#40;fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 Illustre l’utilisation des propriétés ClientSideXML et xsl dans l’application d’une transformation XSL.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration requise pour SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
  
  
