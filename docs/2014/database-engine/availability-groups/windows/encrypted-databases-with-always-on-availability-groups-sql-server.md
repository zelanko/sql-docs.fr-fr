---
title: Chiffrées des bases de données avec des groupes de disponibilité AlwaysOn (SQL Server) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 929206505ffb7aedf292f23e35cbed77ebe4cc20
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142101"
---
# <a name="encrypted-databases-with-alwayson-availability-groups-sql-server"></a>Bases de données chiffrées avec groupes de disponibilité AlwaysOn (SQL Server)
  Cette rubrique contient des informations sur l'utilisation des bases de données actuellement chiffrées ou récemment déchiffrées avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Dans cette rubrique :**  
  
-   [Limitations et restrictions](#Restrictions)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si une base de données est chiffrée ou même contient une clé de chiffrement de base de données (DEK), vous ne pouvez pas utiliser [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] ou [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] pour ajouter la base de données à un groupe de disponibilité. Même si une base de données chiffrée a été déchiffrée, ses sauvegardes de fichiers journaux peuvent contenir des données chiffrées. Dans ce cas, la synchronisation complète initiale des données peut échouer sur la base de données. En effet, l'opération de journalisation de la restauration peut nécessiter le certificat utilisé par les clés de chiffrement de base de données (DEK), et le certificat peut être indisponible.  
  
     Pour qu'une base de données déchiffrée puisse être ajoutée à un groupe de disponibilité, à l'aide de l'Assistant :  
  
    1.  Créez une sauvegarde de fichier journal de la base de données principale.  
  
    2.  Créez une sauvegarde complète de la base de données principale.  
  
    3.  Restaurez la sauvegarde de la base de données sur l'instance de serveur qui héberge le réplica secondaire.  
  
    4.  Créez une nouvelle sauvegarde du journal de la base de données primaire.  
  
    5.  Restaurez cette sauvegarde de journal sur la base de données secondaire.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base de données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Transparent Data Encryption &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  