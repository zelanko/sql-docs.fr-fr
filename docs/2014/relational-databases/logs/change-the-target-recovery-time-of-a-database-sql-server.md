---
title: Modifier la durée de récupération cible d’une base de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 72ac6ac92da531d0f653e0fc03d88d170b7706e5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743215"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a>Modifier la durée de récupération cible d'une base de données (SQL Server)
  Cette rubrique explique comment modifier le temps de récupération cible d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Par défaut, le temps de récupération cible est 0, et la base de données utilise des *points de contrôle automatiques* (qui sont contrôlés par l'option de serveur **intervalle de récupération** ). La définition du temps de récupération cible avec une valeur supérieure à 0 entraîne l'utilisation par la base de données de *points de contrôle indirects* et établit une limite supérieure sur le temps de récupération de cette base de données.  
  
> [!NOTE]  
>  La limite supérieure spécifiée pour une base de données spécifique par son paramètre de temps de récupération cible peut être dépassée si une transaction longue entraîne des durées UNDO excessives.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#Restrictions), [sécurité](#Security)  
  
-   **Pour changer le temps de récupération cible à l’aide de :**  [SQL Server Management Studio](#SSMSProcedure) ou de [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a>  
  
> [!CAUTION]  
>  Une charge de travail transactionnelle en ligne sur une base de données configurée pour les points de contrôle indirects peut rencontrer une dégradation des performances. Les points de contrôle indirects permettent de s’assurer que le nombre de pages de modifications est inférieur à un certain seuil afin que la récupération de la base de données se termine dans le temps de récupération cible. L’option de configuration de l’intervalle de récupération utilise le nombre de transactions pour déterminer le temps de récupération, contrairement aux points de contrôle indirects qui utilisent le nombre de pages de modifications. Quand des points de contrôle indirects sont activés sur une base de données recevant un grand nombre d’opérations DML, l’enregistreur en arrière-plan peut commencer à vider de manière intense les mémoires tampons modifiées sur le disque afin de s’assurer que le délai nécessaire à la récupération se situe dans le temps de récupération cible défini de la base de données. Cela peut entraîner une activité supplémentaire en termes d’E/S sur certains systèmes, ce qui peut contribuer à un goulot d’étranglement des performances si le sous-système du disque fonctionne au-delà du seuil d’E/S ou s’en rapproche.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour modifier le temps de récupération cible**  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Cliquez avec le bouton droit sur la base de données à modifier, puis sélectionnez la commande **Propriétés** .  
  
3.  Dans la boîte de dialogue **Propriétés de la base de données** , cliquez sur la page **Options** .  
  
4.  Dans le volet **Récupération** , dans le champ **Temps de récupération cible (secondes)** , spécifiez le nombre de secondes de votre choix pour définir la limite supérieure du temps de récupération de cette base de données.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour modifier le temps de récupération cible**  
  
1.  Connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où réside la base de données.  
  
2.  Utilisez l'instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)suivante, comme suit :  
  
     TARGET_RECOVERY_TIME **=**_target_recovery_time_ { SECONDS | MINUTES }  
  
     *target_recovery_time*  
     Lorsque la valeur est supérieure à 0 (valeur par défaut), spécifie la limite supérieure du temps de récupération de la base de données spécifiée en cas de sinistre.  
  
     SECONDS  
     Indique que *target_recovery_time* correspond au nombre de secondes.  
  
     MINUTES  
     Indique que *target_recovery_time* correspond au nombre de minutes.  
  
     L'exemple suivant définit le temps de récupération cible de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sur `60` secondes.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Points de contrôle de base de données &#40;SQL Server&#41;](database-checkpoints-sql-server.md)   
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
