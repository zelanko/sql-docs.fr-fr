---
title: Ajouter un rapport personnalisé à Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1496e3abd0be957bdf0b0d2883dacec480fcec12
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "40394410"
---
# <a name="add-a-custom-report-to-management-studio"></a>Ajouter un rapport personnalisé à Management Studio
  Cette rubrique explique comment créer un simple rapport [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enregistré comme fichier .rdl, puis ajouter ce fichier à [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en tant que rapport personnalisé. [!INCLUDE[ssRS](../../includes/ssrs.md)] permet de créer un large choix de rapports élaborés. Pour que vous puissiez créer un rapport en suivant cette rubrique, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] doit être installé sur votre ordinateur. Vous n'avez pas besoin d'installer [!INCLUDE[ssRS](../../includes/ssrs.md)] sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour exécuter un rapport personnalisé à l'aide de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 [Des exemples de rapports](http://go.microsoft.com/fwlink/?LinkId=81792), y compris les rapports standard créés par [!INCLUDE[msCoName](../../includes/msconame-md.md)], peuvent être téléchargés. Vous pouvez modifier ces exemples à l'aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a>Pour créer un rapport simple enregistré en tant que fichier .rdl  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, puis sur **Microsoft SQL Server**, puis cliquez sur **Outils de données SQL Server**.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans la liste **Types de projets** , cliquez sur **Projets Business Intelligence**.  
  
4.  Dans la liste **Modèles** , cliquez sur **Assistant Projet Report Server**.  
  
5.  Dans la zone **Nom**, tapez **ConnectionsReport**, puis cliquez sur **OK**.  
  
6.  Dans la page **Assistant Rapport** , cliquez sur **Suivant**.  
  
7.  Dans la page **Sélectionner la source de données** , dans la zone Nom, entrez un nom de connexion à votre [!INCLUDE[ssDE](../../includes/ssde-md.md)], puis cliquez sur **Modifier**.  
  
8.  Dans la boîte de dialogue **Propriétés de connexion** , dans la zone de texte **Nom du serveur** , tapez le nom de votre instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
9. Dans la zone **Sélectionner ou entrer un nom de base de données** , tapez le nom de l’une de vos bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis cliquez sur **OK**.  
  
10. Dans la page **Sélectionner la source de données** , cliquez sur **Suivant**.  
  
11. Dans la page **Concevoir la requête** , dans la zone **Chaîne de requête** , tapez l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante qui répertorie les connexions en cours à votre [!INCLUDE[ssDE](../../includes/ssde-md.md)], puis cliquez sur **Suivant**. La zone Chaîne de requête de l'Assistant Rapport n'accepte pas les paramètres de rapport. Les rapports personnalisés plus complexes doivent être créés manuellement.  
  
     `SELECT session_id, net_transport FROM sys.dm_exec_connections;`  
  
12. Dans la page **Sélectionner le type de rapport** , sélectionnez **Tabulaire**, puis cliquez sur **Terminer**.  
  
13. Dans la page **Fin de l’Assistant** , dans la zone **Nom du rapport** , tapez **ConnectionsReport**, puis cliquez sur **Terminer** pour créer et enregistrer le rapport.  
  
14. Fermez [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
15. Copiez **ConnectionsReport.rdl** dans un dossier que vous avez créé sur votre serveur de bases de données pour les rapports personnalisés.  
  
### <a name="to-add-a-report-to-management-studio"></a>Pour ajouter un rapport à Management Studio  
  
-   Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], cliquez avec le bouton droit sur un nœud dans l’Explorateur d’objets, pointez sur **Rapports**, puis cliquez sur **Rapports personnalisés**. Dans la boîte de dialogue **Ouvrir un fichier** , recherchez le dossier des rapports personnalisés, sélectionnez le fichier **ConnectionsReport.rdl** , puis cliquez sur **Ouvrir**.  
  
     Quand un nouveau rapport personnalisé est ouvert pour la première fois depuis un nœud de l’Explorateur d’objets, il vient s’ajouter à la liste des derniers fichiers utilisés sous **Rapports personnalisés** dans le menu contextuel de ce nœud. Un rapport standard s’affiche aussi dans la liste des derniers rapports utilisés sous **Rapports personnalisés**quand vous l’ouvrez pour la première fois. En cas de suppression d'un fichier de rapport personnalisé, lorsque l'élément est à nouveau sélectionné, une invite apparaît et propose de supprimer l'élément de la liste des derniers fichiers utilisés.  
  
    1.  Pour modifier le nombre de fichiers dévoilés dans la liste des derniers fichiers utilisés, cliquez sur **Options** dans le menu **Outils** , développez le dossier **Environnement** , puis cliquez sur **Général**.  
  
    2.  Ajustez le nombre de fichiers dans la **liste des derniers fichiers utilisés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Rapports personnalisés dans Management Studio](custom-reports-in-management-studio.md)   
 [Utiliser des rapports personnalisés avec les propriétés de nœud objet Explorateur](use-custom-reports-with-object-explorer-node-properties.md)   
 [Annuler la suppression avertissements d’exécution de rapports personnalisés](unsuppress-run-custom-report-warnings.md)   
 [Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
