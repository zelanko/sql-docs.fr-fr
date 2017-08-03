---
title: "Définir l’arrêt de l’exécution d’un travail (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: df7d516501546d36ac3fac900d694e1e32e2f336
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Définir l'arrêt de l'exécution d'un travail (SQL Server Management Studio)
Cette rubrique explique comment définir le délai pendant lequel [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit attendre la fin de l'exécution des travaux avant la fin de l'exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent lui-même dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour définir une heure d'arrêt pour un travail de SQL Server Agent, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Autorisations  
Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent définir la durée pendant laquelle [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit attendre la fin de l’exécution des travaux avant la fin de l’exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent lui-même. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>Pour définir l'arrêt de l'exécution d'un travail  
  
1.  Dans **l’Explorateur d'objets,** , cliquez sur le signe plus pour développer le serveur sur lequel vous souhaitez définir un intervalle d'arrêt d'exécution d'un travail.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Sous **Sélectionner une page**, sélectionnez **Système de travaux**.  
  
4.  Définissez **l’intervalle du délai d’arrêt** en secondes pour augmenter ou réduire l’intervalle d’arrêt. Cette valeur détermine le délai d'attente pendant lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent attend la fin de l'exécution des travaux avant la fin de l'exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent lui-même.  
  

