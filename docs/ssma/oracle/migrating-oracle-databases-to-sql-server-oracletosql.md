---
title: "Bases de données de migration d’Oracle vers SQL Server (OracleToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Active
ms.openlocfilehash: 738c705c98d1545aff2514802ac3403f66f83571
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Bases de données Oracle migration vers SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) pour Oracle est un environnement complet qui vous permet de migrer rapidement des bases de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure. À l’aide de SSMA pour Oracle, vous pouvez examiner les objets de base de données et les données, évaluer les bases de données pour la migration, migrer des objets de base de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure, puis migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure. Notez que vous ne pouvez pas migrer les schémas SYS et le système Oracle.  
  
## <a name="recommended-migration-process"></a>Processus de Migration recommandé  
Pour pouvoir migrer des objets et des données à partir de bases de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou Azure SQL DB, procédez comme suit :  
  
1.  [Créez un projet SSMA](http://msdn.microsoft.com/en-us/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b).  
  
    Après avoir créé le projet, vous pouvez définir les options de mappage de type, de migration et de conversion de projet. Pour plus d’informations sur les paramètres de projet, consultez [définition des Options de projet &#40; OracleToSQL &#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [Oracle de mappage et les Types de données SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Se connecter au serveur de base de données Oracle](http://msdn.microsoft.com/en-us/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
3.  [Connectez-vous à une instance de SQL Server](http://msdn.microsoft.com/en-us/1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
4.  [Mapper des schémas de base de données Oracle pour les schémas de base de données SQL Server](http://msdn.microsoft.com/en-us/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc).  
  
5.  Si vous le souhaitez, [créer des rapports d’évaluation](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357) pour évaluer des objets de base de données pour la conversion et estimer le temps de conversion.  
  
6.  [Convertir des schémas de base de données Oracle en schémas SQL Server](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272).  
  
7.  [Charger les objets de base de données convertie dans SQL Server](http://msdn.microsoft.com/en-us/a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
    Pour cela, dans une des manières suivantes :  
  
    -   Enregistrer un script et exécutez-le en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Synchroniser les objets de base de données.  
  
8.  [Migrer les données vers SQL Server](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
9. Si nécessaire, mettez à jour des applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[L’installation de SSMA pour Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Prise en main de SSMA pour Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
