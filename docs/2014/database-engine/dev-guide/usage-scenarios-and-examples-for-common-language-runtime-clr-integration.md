---
title: Scénarios et exemples d’utilisation pour l’intégration du Common Language Runtime (CLR) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- scenarios [CLR integration]
- common language runtime [SQL Server], samples
- examples [CLR integration]
- sample applications [CLR integration]
- database objects [CLR integration], samples
- managed code [SQL Server], samples
ms.assetid: 33aac25f-abb4-4f29-af88-4a0dacd80ae7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3718a084211e7c3b2b7a14973e195a4b1c3b6b1a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62780722"
---
# <a name="usage-scenarios-and-examples-for-common-language-runtime-clr-integration"></a>Scénarios et exemples d'utilisation pour l'intégration du CLR (Common Language Runtime)
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient des exemples d'applications et de packages, ainsi que de nombreux exemples de code que vous pouvez utiliser pour apprendre à vous servir des fonctionnalités de programmabilité de l'intégration du CLR.  
  
 Pour obtenir des projets Visual Studio complets qui implémentent ces exemples et des documents supplémentaires, visitez [Microsoft SQL Server projets de la communauté & exemples sur CodePlex](https://go.microsoft.com/fwlink/?LinkID=193935).  
  
|Name|Description|  
|----------|-----------------|  
|[Accès au code natif depuis une fonction CLR définie par l'utilisateur](../../../2014/database-engine/dev-guide/accessing-native-code-from-a-clr-udf.md)|Indique comment appeler une fonction dans du code C++ natif (non managé) à partir d'une fonction définie par l'utilisateur dans un assembly de votre base de données.|  
|[Exemple de paramètre tableau](../../../2014/database-engine/dev-guide/array-parameter-sample.md)|Montre comment créer, mettre à jour ou supprimer un ensemble de lignes dans une base de données en passant un tableau d'informations d'un client à une procédure stockée d'intégration du CLR sur le serveur. Pour cela, un type UDT est utilisé.|  
|[Exemple de type de date et d’heure prenant en compte le calendrier](../../../2014/database-engine/dev-guide/calendar-aware-date-and-time-udt-sample.md)|Définit deux types UDT qui assurent la gestion prenant en charge le calendrier des dates et des heures.|  
|[Exemple de transactions CLR](../../../2014/database-engine/dev-guide/clr-transactions-sample.md)|Montre comment contrôler les transactions à l'aide des API managées situées dans l'espace de noms System.Transactions.|  
|[Création de contacts à l'aide de CLR et XML](../../../2014/database-engine/dev-guide/contact-creation-using-clr-and-xml.md)|L'exemple Contact pour SQL Server fournit quelques utilitaires pratiques qui forment une couche supplémentaire de fonctionnalités en plus de l'exemple de base de données AdventureWorks2012. Le premier utilitaire crée des enregistrements de contact pour les diverses catégories de personnes impliquées dans la base de données AdventureWorks2012. Les informations de contact sont spécifiées à l'aide de XML et passées à une procédure stockée VB ou basée sur C# afin de créer le code XML et le placer dans les tables appropriées avec la base de données.|  
|[Type de devise et fonction de conversion](../../../2014/database-engine/dev-guide/currency-type-and-conversion-function.md)|Définit un type de données Currency défini par l'utilisateur à l'aide de C#.|  
|[Gestion d'objets volumineux à l'aide de CLR](../../../2014/database-engine/dev-guide/handling-large-objects-using-clr.md)|Montre comment transférer des objets blob (Binary Large Object) entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un système de fichiers accessible au serveur au moyen de procédures stockées CLR.|  
|[Exemple HelloWorldReady](../../../2014/database-engine/dev-guide/hello-world-ready-sample.md)|Montre les opérations de base à effectuer pour créer, déployer et tester une procédure stockée simple, basée sur l'intégration du CLR et adaptée à une utilisation internationale.|  
|[Exemple Hello World](../../../2014/database-engine/dev-guide/hello-world-sample.md)|Montre les opérations de base pour créer, déployer et tester une procédure stockée simple basée sur l’intégration du CLR.|  
|[Exemple d'accès aux données in-process](../../../2014/database-engine/dev-guide/in-process-data-access-sample.md)|Contient des fonctions simples illustrant diverses fonctionnalités du fournisseur d'accès aux données in-process du CLR.|  
|[Exemple de jeu de résultats](../../../2014/database-engine/dev-guide/result-set-sample.md)|Montre comment exécuter des commandes tout en lisant les résultats d'une requête, sans ouvrir de nouvelle connexion ni charger tous les résultats en mémoire.|  
|[Exemple Send DataSet](../../../2014/database-engine/dev-guide/send-dataset-sample.md)|Montre comment retourner un DataSet ADO.NET dans une procédure stockée CLR côté client en jeu de résultats au client.|  
|[Exemple de fonctions d'utilitaire de chaîne](../../../2014/database-engine/dev-guide/string-utility-functions-sample.md)|Contient une fonction table en continu, écrite en Visual C# et Visual Basic, qui fractionne une chaîne séparée par des virgules en table à une colonne.|  
|[Exemple de manipulation de chaînes sensible aux caractères supplémentaires](../../../2014/database-engine/dev-guide/supplementary-aware-string-manipulation-sample.md)|Montre la mise en œuvre de cinq fonctions de chaîne [!INCLUDE[tsql](../../includes/tsql-md.md)] sensibles aux caractères supplémentaires capables de traiter à la fois des chaînes Unicode et de substitution.|  
|[Utilitaires UDT](../../../2014/database-engine/dev-guide/udt-utilities.md)|Contient des fonctions utilitaires de types de données définis par l'utilisateur (UDT).|  
|[Nettoyage d'assembly inutilisé](../../../2014/database-engine/dev-guide/unused-assembly-cleanup.md)|Contient une procédure stockée .NET qui supprime des assemblys inutilisés dans la base de données actuelle en interrogeant les catalogues de métadonnées.|  
|[Type défini par l’utilisateur](../../../2014/database-engine/dev-guide/user-defined-type.md)|Montre la création et l'utilisation d'un type UDT simple à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] et d'une application cliente utilisant System.Data.SqlClient.|  
|[Chaîne UTF8 type de données défini par l’utilisateur &#40;UDT&#41;](../../../2014/database-engine/dev-guide/utf8-string-user-defined-data-type-udt.md)|Montre la mise en œuvre d'un type UDT qui étend le système de types de la base de données pour assurer le stockage des valeurs encodées en UTF8.|  
  
  
