---
title: Scénarios d’utilisation et des exemples pour l’intégration du Common Language Runtime (CLR) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- scenarios [CLR integration]
- common language runtime [SQL Server], samples
- examples [CLR integration]
- sample applications [CLR integration]
- database objects [CLR integration], samples
- managed code [SQL Server], samples
ms.assetid: 33aac25f-abb4-4f29-af88-4a0dacd80ae7
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ead4b8976a05e2f27ed4e3f5f44e5de57abfe806
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042966"
---
# <a name="usage-scenarios-and-examples-for-common-language-runtime-clr-integration"></a>Scénarios et exemples d'utilisation pour l'intégration du CLR (Common Language Runtime)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient des exemples d'applications et de packages, ainsi que de nombreux exemples de code que vous pouvez utiliser pour apprendre à vous servir des fonctionnalités de programmabilité de l'intégration du CLR.  
  
 Pour les projets Visual Studio terminées mise en œuvre de ces exemples et la documentation supplémentaire, visitez [Microsoft SQL Server Community Projects & Samples sur CodePlex](http://go.microsoft.com/fwlink/?LinkID=193935).  
  
|Nom   |Description|  
|----------|-----------------|  
|[Accès au Code natif à partir d’un fichier UDF CLR](../../../2014/database-engine/dev-guide/accessing-native-code-from-a-clr-udf.md)|Indique comment appeler une fonction dans du code C++ natif (non managé) à partir d'une fonction définie par l'utilisateur dans un assembly de votre base de données.|  
|[Exemple de paramètre tableau](../../../2014/database-engine/dev-guide/array-parameter-sample.md)|Montre comment créer, mettre à jour ou supprimer un ensemble de lignes dans une base de données en passant un tableau d'informations d'un client à une procédure stockée d'intégration du CLR sur le serveur. Pour cela, un type UDT est utilisé.|  
|[Exemple d’UDT prenant en charge Calendar Date et heure](../../../2014/database-engine/dev-guide/calendar-aware-date-and-time-udt-sample.md)|Définit deux types UDT qui assurent la gestion prenant en charge le calendrier des dates et des heures.|  
|[Exemple de Transactions CLR](../../../2014/database-engine/dev-guide/clr-transactions-sample.md)|Montre comment contrôler les transactions à l'aide des API managées situées dans l'espace de noms System.Transactions.|  
|[Création de contact à l’aide du CLR et XML](../../../2014/database-engine/dev-guide/contact-creation-using-clr-and-xml.md)|L'exemple Contact pour SQL Server fournit quelques utilitaires pratiques qui forment une couche supplémentaire de fonctionnalités en plus de l'exemple de base de données AdventureWorks2012. Le premier utilitaire crée des enregistrements de contact pour les diverses catégories de personnes impliquées dans la base de données AdventureWorks2012. Les informations de contact sont spécifiées à l'aide de XML et passées à une procédure stockée VB ou basée sur C# afin de créer le code XML et le placer dans les tables appropriées avec la base de données.|  
|[Type de devise et fonction de Conversion](../../../2014/database-engine/dev-guide/currency-type-and-conversion-function.md)|Définit un type de données Currency défini par l'utilisateur à l'aide de C#.|  
|[Gestion d’objets volumineux à l’aide du CLR](../../../2014/database-engine/dev-guide/handling-large-objects-using-clr.md)|Montre comment transférer des objets blob (Binary Large Object) entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un système de fichiers accessible au serveur au moyen de procédures stockées CLR.|  
|[Exemple helloworldready](../../../2014/database-engine/dev-guide/hello-world-ready-sample.md)|Montre les opérations de base à effectuer pour créer, déployer et tester une procédure stockée simple, basée sur l'intégration du CLR et adaptée à une utilisation internationale.|  
|[Exemple Hello World](../../../2014/database-engine/dev-guide/hello-world-sample.md)|Montre les opérations de base pour créer, déployer et tester une simple CLR basée sur l’intégration procédure stockée.|  
|[Exemple d’accès aux données in-Process](../../../2014/database-engine/dev-guide/in-process-data-access-sample.md)|Contient des fonctions simples illustrant diverses fonctionnalités du fournisseur d'accès aux données in-process du CLR.|  
|[Exemple de jeu de résultats](../../../2014/database-engine/dev-guide/result-set-sample.md)|Montre comment exécuter des commandes tout en lisant les résultats d'une requête, sans ouvrir de nouvelle connexion ni charger tous les résultats en mémoire.|  
|[Exemple Send DataSet](../../../2014/database-engine/dev-guide/send-dataset-sample.md)|Montre comment retourner un DataSet ADO.NET dans une procédure stockée CLR côté client en jeu de résultats au client.|  
|[Exemple de chaîne de fonctions utilitaires](../../../2014/database-engine/dev-guide/string-utility-functions-sample.md)|Contient une fonction table en continu, écrite en Visual C# et Visual Basic, qui fractionne une chaîne séparée par des virgules en table à une colonne.|  
|[Exemple de Manipulation de chaîne supplémentaires prenant en charge](../../../2014/database-engine/dev-guide/supplementary-aware-string-manipulation-sample.md)|Montre la mise en œuvre de cinq fonctions de chaîne [!INCLUDE[tsql](../../includes/tsql-md.md)] sensibles aux caractères supplémentaires capables de traiter à la fois des chaînes Unicode et de substitution.|  
|[Utilitaires UDT](../../../2014/database-engine/dev-guide/udt-utilities.md)|Contient des fonctions utilitaires de types de données définis par l'utilisateur (UDT).|  
|[Nettoyage d’Assembly inutilisé](../../../2014/database-engine/dev-guide/unused-assembly-cleanup.md)|Contient une procédure stockée .NET qui supprime des assemblys inutilisés dans la base de données actuelle en interrogeant les catalogues de métadonnées.|  
|[Type défini par l’utilisateur](../../../2014/database-engine/dev-guide/user-defined-type.md)|Montre la création et l'utilisation d'un type UDT simple à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] et d'une application cliente utilisant System.Data.SqlClient.|  
|[UTF8 Type de données défini par l’utilisateur de chaîne &#40;UDT&#41;](../../../2014/database-engine/dev-guide/utf8-string-user-defined-data-type-udt.md)|Montre la mise en œuvre d'un type UDT qui étend le système de types de la base de données pour assurer le stockage des valeurs encodées en UTF8.|  
  
  