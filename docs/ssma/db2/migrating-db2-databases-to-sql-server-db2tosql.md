---
title: Bases de données de migration de DB2 vers SQL Server (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 26b95bc37f1ba7726c607e6275889ecd6a3fecd9
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40394864"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Migration des bases de données de DB2 vers SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour DB2 est un environnement complet qui vous permet de migrer rapidement des bases de données DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. À l’aide de SSMA pour DB2, vous pouvez passer en revue les objets de base de données et de données, évaluer les bases de données pour la migration, migrer des objets de base de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, et migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Notez que vous ne pouvez pas migrer les schémas SYS et système DB2.  
  
## <a name="recommended-migration-process"></a>Processus de Migration recommandé  
Pour pouvoir migrer des objets et des données à partir de bases de données DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Azure SQL DB, utilisez le processus suivant :  
  
1.  [Nouveau projet SSMA](http://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0).  
  
    Après avoir créé le projet, vous pouvez définir les options de mappage de type, la migration et la conversion du projet. Pour plus d’informations sur les paramètres de projet, consultez [paramètres du projet &#40;Conversion&#41; &#40;DB2ToSQL&#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) et rubriques connexes. Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [DB2 de mappage et les Types de données SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  [Se connecter à la base de données DB2](http://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
3.  [Connexion à SQL Server](http://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
4.  [Mapper des schémas DB2 à des schémas SQL Server](http://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a).  
  
5.  Si vous le souhaitez, [des rapports d’évaluation](http://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de) pour évaluer certains objets de base de données pour la conversion et estimer le temps de conversion.  
  
6.  [Convertir des schémas DB2](http://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0).  
  
7.  [Charger les objets de base de données convertis dans SQL Server](http://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
    Vous pouvez effectuer cela dans une des manières suivantes :  
  
    -   Enregistrer un script et exécutez-le dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Synchroniser les objets de base de données.  
  
8.  [Migration de données DB2 dans SQL Server](http://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
9. Si nécessaire, mettre à jour des applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Bien démarrer avec SSMA pour DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
