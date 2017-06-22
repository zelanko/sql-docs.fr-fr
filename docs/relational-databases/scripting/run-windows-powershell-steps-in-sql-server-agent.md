---
title: "Utiliser Windows PowerShell dans les étapes de travail de l’Agent SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f25f7549-c9b3-4618-85f2-c9a08adbe0e3
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ae35fb3deecc8b77940ab76d1b0f016f00f39e27
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="run-windows-powershell-steps-in-sql-server-agent"></a>Utiliser Windows PowerShell dans les étapes de travail de l'Agent SQL Server
  Utilisez SQL Server Agent pour exécuter des scripts PowerShell SQL Server à des horaires planifiés.  
  
1.  **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)  
  
2.  **To run PowerShell from SQL Server Agent, using:**  [PowerShell Job Step](#PShellJob), [Command Prompt Job Step](#CmdExecJob)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Il y a plusieurs types d'étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Chaque type est associé à un sous-système qui implémente un environnement spécifique, tel qu'un agent de réplication ou un environnement d'invite de commandes. Vous pouvez coder les scripts Windows PowerShell, puis utiliser l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les inclure dans les travaux qui s'exécutent à des heures planifiées ou en réponse à des événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les scripts Windows PowerShell peuvent être exécutés à l'aide d'une étape de travail d'invite de commandes ou d'une étape de travail PowerShell.  
  
1.  Utilisez une étape du travail PowerShell pour que le sous-système de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent exécute l’utilitaire **sqlps** , qui lance PowerShell 2.0 et importe le module **sqlps** .  
  
2.  Utilisez une étape du travail d’invite de commandes pour exécuter PowerShell.exe et spécifiez un script qui importe le module **sqlps** .  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
  
> [!CAUTION]  
>  Chaque étape de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécute PowerShell avec le module **sqlps** lance un processus qui consomme environ 20 Mo de mémoire. L'exécution simultanée d'un grand nombre d'étapes de travail Windows PowerShell peut nuire aux performances.  
  
##  <a name="PShellJob"></a> Créer une étape de travail PowerShell  
 **Pour créer une étape de travail PowerShell**  
  
1.  Développez **SQL Server Agent**, créez un travail ou cliquez avec le bouton droit de la souris sur un travail existant, puis cliquez sur **Propriétés**. Pour plus d'informations sur la création d'un travail, consultez [Création de travaux](http://msdn.microsoft.com/library/465fb7fc-7622-4252-a178-ea51691c935b).  
  
2.  Dans la boîte de dialogue **Propriétés du travail** , cliquez sur la page **Étapes** , puis sur **Nouveau**.  
  
3.  Dans la boîte de dialogue **Nouvelle étape du travail** , tapez un **nom d'étape**de travail.  
  
4.  Dans la liste **Type** , cliquez sur **PowerShell**.  
  
5.  Dans la liste **Exécuter en tant que** , sélectionnez le compte proxy avec les informations d'identification que le travail utilisera.  
  
6.  Dans la zone **Commande** , tapez la syntaxe du script PowerShell qui sera exécuté pour l'étape de travail. Vous pouvez aussi cliquer sur **Ouvrir** et sélectionner un fichier contenant la syntaxe du script.  
  
7.  Cliquez sur la page **Avancé** pour paramétrer les options suivantes pour l'étape de travail : l'action à exécuter si l'étape de travail échoue ou réussit, le nombre de tentatives d'exécution de l'étape de travail que doit effectuer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la fréquence de ces tentatives.  
  
##  <a name="CmdExecJob"></a> Créer une étape de travail d'invite de commandes  
 **Pour créer une étape de travail CmdExec**  
  
1.  Développez **SQL Server Agent**, créez un travail ou cliquez avec le bouton droit de la souris sur un travail existant, puis cliquez sur **Propriétés**. Pour plus d'informations sur la création d'un travail, consultez [Création de travaux](http://msdn.microsoft.com/library/465fb7fc-7622-4252-a178-ea51691c935b).  
  
2.  Dans la boîte de dialogue **Propriétés du travail** , cliquez sur la page **Étapes** , puis sur **Nouveau**.  
  
3.  Dans la boîte de dialogue **Nouvelle étape du travail** , tapez un **nom d'étape**de travail.  
  
4.  Dans la liste **Type** , choisissez **Système d’exploitation (CmdExec)**.  
  
5.  Dans la liste **Exécuter en tant que** , sélectionnez le compte proxy avec les informations d'identification que doit utiliser le travail. Par défaut, les étapes de travail CmdExec s'exécutent dans le contexte du compte de service SQL Server Agent.  
  
6.  Dans la zone **Traiter le code de sortie d'une commande réussie** , entrez une valeur comprise entre 0 et 999999.  
  
7.  Dans la zone **Commande** , entrez powershell.exe avec des paramètres spécifiant le script PowerShell à exécuter.  
  
8.  Cliquez sur la page **Avancé** pour définir les options d'étape de travail, telles que l'action à exécuter lorsque l'étape de travail aboutit ou échoue, le nombre de tentatives d'exécution de l'étape de travail que doit effectuer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le fichier où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut écrire la sortie de l'étape de travail. Seuls les membres du rôle fixe **sysadmin** peuvent écrire la sortie d'étape de travail dans un fichier du système d'exploitation.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
