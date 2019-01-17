---
title: Ajouter une base de données chiffrée à un groupe de disponibilité
description: Procédure à suivre pour ajouter une base de données chiffrée (ou récemment déchiffrée) à un groupe de disponibilité Always On.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf22a6a15d85f3e5ad6ffc24a9ce371f43b34206
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215485"
---
# <a name="add-an-encrypted-database-to-an-always-on-availability-group"></a>Ajouter une base de données chiffrée à un groupe de disponibilité Always On
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
  
-   [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base de données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Chiffrement transparent des données &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
