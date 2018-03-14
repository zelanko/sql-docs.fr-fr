---
title: "Didacticiel : Préparation du serveur à la réplication | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3f7055cc15673a5dfd4564f26c4d314ccc0f5180
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="tutorial-preparing-the-server-for-replication"></a>Didacticiel : Préparation du serveur à la réplication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Il importe de prévoir la sécurité avant de configurer la topologie de réplication. Ce didacticiel vous explique comment sécuriser au mieux une topologie de réplication et configurer la distribution, première étape de la réplication des données. Ce didacticiel doit être effectué avant les autres didacticiels.  
  
> [!NOTE]  
> Pour répliquer les données de façon sécurisée entre les serveurs, vous devez implémenter l’ensemble des recommandations des [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
Dans ce didacticiel, vous allez apprendre à préparer un serveur afin que la réplication puisse s'exécuter de façon sécurisée avec les privilèges minimaux. La première leçon explique comment créer les comptes de service Windows utilisés pour exécuter les agents de réplication. La deuxième leçon montre comment configurer le dossier utilisé pour générer et stocker les instantanés de publication. La troisième leçon vous apprend à configurer la distribution et à définir les autorisations.  
  
## <a name="requirements"></a>Spécifications  
Ce didacticiel est destiné aux utilisateurs qui sont familiers des opérations essentielles de base de données, mais dont l'expérience en matière de réplication est limitée.  
  
Pour utiliser ce didacticiel, les composants suivants doivent être installés sur votre système :  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] avec la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
**Durée estimée pour effectuer ce didacticiel : 30 minutes.**  
  
## <a name="lessons-in-this-tutorial"></a>Leçons du didacticiel  
  
-   [Leçon 1 : Création de comptes Windows pour la réplication](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [Leçon 2 : Préparation du dossier d'instantanés](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md)  
  
-   [Leçon 3 : Configuration de la distribution](../../relational-databases/replication/lesson-3-configuring-distribution.md)  
  
[Démarrer le didacticiel](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a> Voir aussi  
[Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
[Sécurité et protection &#40;Réplication&#41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
  
