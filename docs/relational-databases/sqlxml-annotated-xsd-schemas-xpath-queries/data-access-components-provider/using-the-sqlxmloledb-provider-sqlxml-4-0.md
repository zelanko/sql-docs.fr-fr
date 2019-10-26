---
title: Utilisation du fournisseur SQLXMLOLEDB (SQLXML 4,0) | Microsoft Docs
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9bc5e79f52f3aabbe157065db86e8d0968537ef7
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909355"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>Utilisation du fournisseur SQLXMLOLEDB (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les rubriques de cette section présentent des exemples d'application ADO qui illustrent l'utilisation des propriétés spécifiques au fournisseur SQLXMLOLEDB.  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>Spécifications de l'application pour le fournisseur SQLXMLOLEDB 4.0  
 Pour créer des exemples fonctionnels qui utilisent SQLXMLOLEDB 4.0, vous devez effectuer les opérations suivantes :  
  
1.  Créer une application Microsoft Visual Basic.exe et ajouter l'une des références suivantes :  
  
    -   Bibliothèque Microsoft ActiveX Data Objects 2,6  
  
    -   Bibliothèque Microsoft ActiveX Data Objects 2,7  
  
    -   Bibliothèque Microsoft ADO 2.8  
  
2.  Déployer et installer SQLXML 4.0 et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  

     Pour plus d’informations, consultez les [concepts de programmation de SQLXML 4,0](../../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md) et [installation de SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exécution du fournisseur SQLXMLOLEDB &#40;de requêtes SQL&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md)  
 Illustre l’utilisation des propriétés racine ClientSideXML et XML pour exécuter des requêtes SQL.  
  
 [Exécution de modèles contenant des requêtes &#40;SQL fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 Illustre l’utilisation de la propriété ClientSideXML.  
  
 [Exécution de requêtes &#40;XPath (fournisseur SQLXMLOLEDB)&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md)  
 Illustre l’utilisation des propriétés ClientSideXML, chemin de base et schéma de mappage.  
  
 [Exécution de requêtes XPath avec des espaces &#40;de noms fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 Illustre la procédure d'interrogation sur des schémas qualifiés par un espace de noms.  
  
 [Exécution de modèles contenant des requêtes &#40;XPath fournisseur SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 Montre comment exécuter des modèles avec des requêtes SQL à l’aide des propriétés ClientSideXML, chemin de base et schéma de mappage.  
  
 [Application d’un fournisseur &#40;SQLXMLOLEDB de transformation XSL&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 Illustre l’utilisation des propriétés ClientSideXML et xsl lors de l’application d’une transformation XSL.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration requise pour SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
  
  
