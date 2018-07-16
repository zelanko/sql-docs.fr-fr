---
title: Spécifier la copie ou l’interrogation de table (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 44d7dfcb5928d0984c0ce34b314fd4d25adcc812
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264945"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a>Spécifier la copie ou l'interrogation de table (Assistant Importation et Exportation SQL Server)
  Utilisez le **spécifier la copie de Table ou requête** page pour spécifier comment copier des données. Vous pouvez utiliser une interface graphique pour sélectionner les objets de base de données existants à copier ou avoir recours à Transact-SQL pour créer une requête plus complexe.  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Copier les données à partir d’une ou plusieurs tables ou vues**  
 Copier les champs des tables source sélectionné et des vues pour l’ou les destinations spécifiées à l’aide de la **sélectionner les Tables Source et vues** boîte de dialogue. Utilisez cette option si vous souhaitez copier toutes les données dans la source sans effectuer de tri ou de filtrage sur les enregistrements.  
  
 Lorsque vous utilisez un [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournisseur de données pour se connecter à votre source de données, le **copier des données à partir d’une ou plusieurs tables ou vues** option n’est peut-être pas disponible. Cette option est disponible uniquement pour les fournisseurs qui disposent d'une section ProviderDescription dans le fichier ProviderDescriptors.xml. Chaque section ProviderDescription contient les informations requises pour extraire les métadonnées du fournisseur correspondant. Par défaut, le fichier ProviderDescriptors.xml contient une section ProviderDescription pour les fournisseurs suivants exclusivement :  
  
-   System.Data.SqlClient  
  
-   System.Data.OracleClient  
  
-   System.Data.OleDb  
  
-   System.Data.Odbc  
  
 Pour rendre le **copier des données à partir d’une ou plusieurs tables ou vues** option disponible pour les fournisseurs supplémentaires, de fournisseurs tiers peuvent ajouter leur propre section providerdescriptor au fichier ProviderDescriptors.xml. Par défaut, ce fichier se trouve dans \< *lecteur*> : \Program Files\Microsoft SQL Server\100\DTS\ProviderDescriptors. Pour vérifier les spécifications de la section ProviderDescriptor, consultez le fichier de schéma ProviderDescriptors.xsd qui figure par défaut dans le même dossier que le fichier ProviderDescriptors.xml.  
  
 **Écrire une requête pour spécifier les données à transférer**  
 Générez des instructions SQL pour extraire des lignes à l’aide de la **fournir une requête Source** boîte de dialogue. Utilisez cette option si vous souhaitez modifier ou limiter les données source lors de la copie. Seules les lignes correspondant aux critères de sélection peuvent être copiées.  
  
  
