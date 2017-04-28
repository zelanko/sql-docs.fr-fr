---
title: "Définir les options d’une étape de travail Transact-SQL | Microsoft Docs"
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
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4bf48de41b0d89e7b2edc063010bf20826463b22
ms.lasthandoff: 04/11/2017

---
# <a name="define-transact-sql-job-step-options"></a>Définir les options d'une étape de travail Transact-SQL
Cette rubrique explique comment définir les options pour les étapes de travail [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  [!INCLUDE[tsql](../../includes/tsql_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de SQL Server Management Objects.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour définir les options d'une étape de travail Transact-SQL, avec :** ,  
  
    [SQL Server Management Studio](#SSMS)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-define-transact-sql-job-step-options"></a>Pour définir les options d'une étape de travail Transact-SQL  
  
1.  Dans **l'Explorateur d'objets**, développez **Agent SQL Server**, développez **Travaux**, cliquez avec le bouton droit sur le travail que vous voulez modifier, puis cliquez sur **Propriétés**.  
  
2.  Cliquez successivement sur la page **Étapes** , sur une étape de travail et sur **Modifier**.  
  
3.  Dans la boîte de dialogue **Propriétés de l'étape de travail** , confirmez le type de travail **Script Transact-SQL (TSQL)**, puis sélectionnez la page **Avancé** .  
  
4.  Définissez l'action à exécuter si le travail aboutit en sélectionnant l'option appropriée dans la liste **Action en cas de succès** .  
  
5.  Définissez le nombre de tentatives en entrant un nombre compris entre 0 et 9999 dans la zone **Tentatives de reprises** .  
  
6.  Définissez une fréquence de tentative en entrant un nombre de minutes compris entre 0 et 9999 dans la zone **Intervalle de reprise** .  
  
7.  Définissez l'action à exécuter si le travail échoue en sélectionnant l'option appropriée dans la liste **Action en cas d'échec** .  
  
8.  Si le travail est un script [!INCLUDE[tsql](../../includes/tsql_md.md)] , vous pouvez choisir les options suivantes :  
  
    -   Entrez le nom d'un **fichier de sortie**. Par défaut, les données du fichier sont remplacées chaque fois que l'étape de travail s'exécute. Si vous ne voulez pas remplacer les données, activez **Ajouter la sortie au fichier existant**. Cette option est uniquement disponible pour les membres du rôle de serveur fixe **sysadmin** . Notez que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ne permet pas aux utilisateurs d'afficher les fichiers arbitraires dans le système de fichiers. Vous ne pouvez donc pas utiliser [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] pour afficher les journaux d'étape de travail écrits dans le système de fichiers.  
  
    -   Activez **Enregistrer un journal dans la table** pour enregistrer l'étape de travail dans une table de base de données. Par défaut, le contenu de la table est remplacé chaque fois que l'étape de travail s'exécute. Si vous ne voulez pas remplacer les données, activez **Ajouter la sortie à l'entrée existante dans la table**. Une fois l'étape de travail exécutée, vous pouvez afficher le contenu de la table en cliquant sur **Afficher**.  
  
    -   Activez **Inclure la sortie de l'étape dans l'historique** pour inclure la sortie dans l'historique de l'étape. Le résultat ne sera affiché que s'il n'y a pas d'erreur. De même, le résultat peut être tronqué.  
  
9. Si vous êtes membre du rôle de serveur fixe **sysadmin** et voulez exécuter cette étape de travail avec une connexion SQL différente, sélectionnez la connexion SQL dans la liste **Exécuter en tant qu'utilisateur** .  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour définir les options d'une étape de travail Transact-SQL**  
  
Utilisez la classe **JobStep** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell.  
  

