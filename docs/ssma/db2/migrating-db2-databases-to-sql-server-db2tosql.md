---
title: Migration de bases de données DB2 vers SQL Server (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 79cc961148add0bf2096a716b669199360a565b1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68084655"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Migration de bases de données DB2 vers SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Assistant Migration (SSMA) pour DB2 est un environnement complet qui vous aide à migrer rapidement des bases [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données DB2 vers ou Azure SQL db. En utilisant SSMA pour DB2, vous pouvez examiner les données et les objets de base de données, évaluer les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la migration, migrer des objets de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données vers ou Azure SQL dB, puis migrer des données vers ou Azure SQL db. Notez que vous ne pouvez pas migrer les schémas SYS et système DB2.  
  
## <a name="recommended-migration-process"></a>Processus de migration recommandé  
Pour migrer des objets et des données de bases de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données DB2 vers ou Azure SQL dB, procédez comme suit :  
  
1.  [Nouveau projet SSMA](https://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0).  
  
    Après avoir créé le projet, vous pouvez définir les options de conversion de projet, de migration et de mappage de type. Pour plus d’informations sur les paramètres de projet, consultez [paramètres du projet &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) et les sections associées. Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [mappage des types de données DB2 et SQL Server &#40;&#41;DB2ToSQL ](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  [Connectez-vous à la base de données DB2](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
3.  [Connexion à SQL Server](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
4.  [Mappez les schémas DB2 aux schémas de SQL Server](https://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a).  
  
5.  Éventuellement, des [rapports d’évaluation](https://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de) pour évaluer les objets de base de données pour la conversion et estimer la durée de la conversion.  
  
6.  [Convertissez les schémas DB2](https://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0).  
  
7.  [Chargez les objets de base de données convertis dans SQL Server](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
    Vous pouvez le faire de l’une des manières suivantes :  
  
    -   Enregistrez un script et exécutez-le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans.  
  
    -   Synchronisez les objets de base de données.  
  
8.  [Migration des données DB2 vers SQL Server](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
9. Si nécessaire, mettez à jour les applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Prise en main avec SSMA pour DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
