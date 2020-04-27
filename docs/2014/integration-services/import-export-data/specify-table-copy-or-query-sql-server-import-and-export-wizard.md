---
title: Spécifier la copie ou l’interrogation de table (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 524e878933652699bef6e31da42d3a784b54df7c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62892641"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a>Spécifier la copie ou l'interrogation de table (Assistant Importation et Exportation SQL Server)
  Utilisez la page **spécifier la copie ou l’interrogation de table** pour spécifier comment copier les données. Vous pouvez utiliser une interface graphique pour sélectionner les objets de base de données existants à copier ou avoir recours à Transact-SQL pour créer une requête plus complexe.  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que sur les autorisations requises pour exécuter correctement l’Assistant, consultez [exécuter l’Assistant importation et exportation SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Copier des données à partir d’une ou plusieurs tables ou vues**  
 Copiez les champs des tables et des vues sources sélectionnées vers la ou les destinations spécifiées à l’aide de la boîte de dialogue **Sélectionner les tables et les vues sources** . Utilisez cette option si vous souhaitez copier toutes les données dans la source sans effectuer de tri ou de filtrage sur les enregistrements.  
  
 Lorsque vous utilisez un [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournisseur de données pour vous connecter à votre source de données, l’option **copier les données à partir d’une ou plusieurs tables ou vues** peut ne pas être disponible. Cette option est disponible uniquement pour les fournisseurs qui disposent d'une section ProviderDescription dans le fichier ProviderDescriptors.xml. Chaque section ProviderDescription contient les informations requises pour extraire les métadonnées du fournisseur correspondant. Par défaut, le fichier ProviderDescriptors.xml contient une section ProviderDescription pour les fournisseurs suivants exclusivement :  
  
-   System.Data.SqlClient  
  
-   System.Data.OracleClient  
  
-   System.Data.OleDb  
  
-   System.Data.Odbc  
  
 Pour que l’option **copier les données à partir d’une ou plusieurs tables ou vues** soit disponible pour des fournisseurs supplémentaires, des tiers peuvent ajouter leurs propres sections ProviderDescriptor au fichier ProviderDescriptors. Xml. Par défaut, ce fichier se trouve \<dans le *lecteur*> : \Program Files\Microsoft SQL Server\100\DTS\ProviderDescriptors. Pour vérifier les spécifications de la section ProviderDescriptor, consultez le fichier de schéma ProviderDescriptors.xsd qui figure par défaut dans le même dossier que le fichier ProviderDescriptors.xml.  
  
 **Écrire une requête pour spécifier les données à transférer**  
 Générez des instructions SQL pour récupérer des lignes à l’aide de la boîte **de dialogue fournir une requête source** . Utilisez cette option si vous souhaitez modifier ou limiter les données source lors de la copie. Seules les lignes correspondant aux critères de sélection peuvent être copiées.  
  
  
