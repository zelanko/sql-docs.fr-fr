---
description: Propriétés de l'étape du travail - Nouvelle étape du travail (page Avancé)
title: Propriétés de la nouvelle étape du travail (page Avancé)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: d4987186486dc6164f9827f03aec8e30e10d40eb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97408853"
---
# <a name="job-step-properties---new-job-step-advanced-page"></a>Propriétés de l'étape du travail - Nouvelle étape du travail (page Avancé)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et changer les propriétés d’une étape de travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Action en cas de succès**  
Définit l'action que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit exécuter si l'étape de travail réussit.  
  
**Nouvelles tentatives**  
Définit le nombre de tentatives effectuées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour reprendre une étape de travail qui a échoué.  
  
**Intervalle de reprise (minutes)**  
Définit le délai d'attente entre les tentatives de reprise par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**Action en cas d'échec**  
Définit l'action que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit exécuter si l'étape de travail échoue.  
  
## <a name="options-for-transact-sql-job-steps"></a>Options des étapes de travail Transact-SQL  
**Fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail. Cette option est disponible uniquement pour les membres du rôle serveur fixe **sysadmin** .  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Afficher**  
Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie au contenu existant du fichier. Sinon, le contenu précédent du fichier est remplacé à chaque exécution de l'étape de travail.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Afficher**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
**Exécuter en tant qu'utilisateur**  
Si vous êtes membre du rôle serveur fixe **sysadmin** , vous pouvez sélectionner une autre connexion SQL pour exécuter cette étape de travail.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Options des étapes de travail du système d'exploitation (CmdExec)  
**Fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail.  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Afficher**  
Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie de l'étape de travail au contenu précédent du fichier à chaque exécution.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Afficher**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="options-for-powershell-job-steps"></a>Options des étapes de travail PowerShell  
**Fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail.  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Afficher**  
Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie de l'étape de travail au contenu précédent du fichier à chaque exécution.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Afficher**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Options des étapes de travail de l'Agent de lecture de file d'attente de la réplication  
**Serveur**  
Définit le serveur à utiliser pour l'étape de travail de l'Agent de lecture de file d'attente de la réplication.  
  
**Sauvegarde de la base de données**  
Définit la base de données à utiliser pour l'étape de travail de l'Agent de lecture de file d'attente de la réplication.  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a>Options des étapes de travail de SQL Server Analysis Services  
**Fichier de sortie**  
Définit le fichier à utiliser comme sortie avec l'étape de travail. Cette option est disponible uniquement pour les membres du rôle serveur fixe **sysadmin** .  
  
**...**  
Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
**Afficher**  
Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
**Ajouter la sortie au fichier existant**  
Ajoute la sortie au contenu existant du fichier. Sinon, le contenu précédent du fichier est remplacé à chaque exécution de l'étape de travail.  
  
**Enregistrer un journal dans la table**  
Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
**Afficher**  
Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
**Ajouter la sortie à l'entrée existante dans la table**  
Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
**Inclure la sortie de l'étape dans l'historique**  
Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="see-also"></a>Voir aussi  
[Gérer les étapes de travail](../../ssms/agent/manage-job-steps.md)  
