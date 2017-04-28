---
title: "Propriétés de l’étape du travail - Nouvelle étape du travail (page Avancé) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ea8ecf39a23a0db715c95bb4041c802a382822fa
ms.lasthandoff: 04/11/2017

---
# <a name="job-step-properties---new-job-step-advanced-page"></a>Propriétés de l'étape du travail - Nouvelle étape du travail (page Avancé)
Utilisez cette page pour afficher et modifier les propriétés d'une étape de travail de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Options  
**Action en cas de succès**  
Définit l'action que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] doit exécuter si l'étape de travail réussit.  
  
**Tentatives de reprises**  
Définit le nombre de tentatives effectuées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pour reprendre une étape de travail qui a échoué.  
  
**Intervalle de reprise (minutes)**  
Définit le délai d'attente entre les tentatives de reprise par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Action en cas d'échec**  
Définit l'action que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] doit exécuter si l'étape de travail échoue.  
  
## <a name="options-for-transact-sql-job-steps"></a>Options des étapes de travail Transact-SQL  
**fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail. Cette option est disponible uniquement pour les membres du rôle serveur fixe **sysadmin** .  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Affichage**  
Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie au contenu existant du fichier. Sinon, le contenu précédent du fichier est remplacé à chaque exécution de l'étape de travail.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Affichage**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
**Exécuter en tant qu'utilisateur**  
Si vous êtes membre du rôle serveur fixe **sysadmin** , vous pouvez sélectionner une autre connexion SQL pour exécuter cette étape de travail.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Options des étapes de travail du système d'exploitation (CmdExec)  
**fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail.  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Affichage**  
Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie de l'étape de travail au contenu précédent du fichier à chaque exécution.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Affichage**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="options-for-powershell-job-steps"></a>Options des étapes de travail PowerShell  
**fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail.  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Affichage**  
Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie de l'étape de travail au contenu précédent du fichier à chaque exécution.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Affichage**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Options des étapes de travail de l'Agent de lecture de file d'attente de la réplication  
**Server**  
Définit le serveur à utiliser pour l'étape de travail de l'Agent de lecture de file d'attente de la réplication.  
  
**Base de données**  
Définit la base de données à utiliser pour l'étape de travail de l'Agent de lecture de file d'attente de la réplication.  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a>Options des étapes de travail de SQL Server Analysis Services  
**fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail. Cette option est disponible uniquement pour les membres du rôle serveur fixe **sysadmin** .  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Affichage**  
Dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie au contenu existant du fichier. Sinon, le contenu précédent du fichier est remplacé à chaque exécution de l'étape de travail.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Affichage**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="see-also"></a>Voir aussi  
[Gérer les étapes de travail](../../ssms/agent/manage-job-steps.md)  
  

