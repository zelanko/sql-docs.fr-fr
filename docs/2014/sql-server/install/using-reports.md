---
title: Utilisation des rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- overriding reports
- Upgrade Advisor Report Viewer
- reports [Upgrade Advisor], about reports
- formatting reports
- resolved issues [Upgrade Advisor]
- distributing reports [Reporting Services]
- filtering reports [Reporting Services]
- removing report items
- viewing reports
- rerunning analysis
- information issues [Upgrade Advisor]
- deleting report items
- icons [Upgrade Advisor]
- Upgrade Advisor [SQL Server], reports
- sending reports
- blocking issues [Upgrade Advisor]
- sharing reports
- reports [Upgrade Advisor]
- SQL Server Upgrade Advisor, reports
- modifying reports
- distributing reports [Reporting Services], about report distribution
- warnings [Upgrade Advisor]
- analyzing system [Upgrade Advisor], reports
ms.assetid: 4a3cb94a-a7ac-4cec-94c7-db26fcf6d161
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f52afcfdaa7de33d83d64a049f9a350f0463b4c6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062344"
---
# <a name="using-reports"></a>Utilisation de rapports
  Un rapport distinct est généré pour chaque composant et, si nécessaire, pour chaque instance, que l'Assistant Analyse du Conseiller de mise à niveau analyse sur un serveur. Le rapport contient des détails sur les problèmes connus qui affectent une mise à niveau. Il fournit également des liens vers des informations et des actions suggérées pour traiter les problèmes identifiés.  
  
> [!NOTE]  
>  Si la visionneuse de rapports du conseiller de mise à niveau ne trouve pas de rapports dans le répertoire des rapports par défaut, vous pouvez charger un rapport à partir d’un répertoire différent à l’aide du lien **ouvrir le rapport** .  
  
## <a name="viewing-reports"></a>Affichage de rapports  
 La visionneuse de rapports vous permet d'afficher les rapports du Conseiller de mise à niveau. Pour afficher les rapports, sur la page de démarrage du conseiller de mise à niveau, cliquez sur **lancer le conseiller de mise à niveau**.  
  
 Après avoir chargé le rapport d'un serveur, vous pouvez sélectionner un composant pour consulter les problèmes de mise à niveau le concernant. Vous pouvez appliquer un filtre à partir de la zone **Filtrer par** pour afficher les éléments suivants :  
  
-   Tous les problèmes  
  
-   Tous les problèmes de mise à niveau  
  
-   Problèmes de pré-mise à niveau  
  
-   Tous les problèmes de migration  
  
-   Problèmes résolus  
  
-   Problèmes non résolus  
  
 Si votre rapport contient plus de 20 problèmes, vous pouvez passer au groupe de problèmes suivant ou précédent en cliquant sur **20 suivants** ou **20 précédents** en haut ou en bas de la liste des problèmes.  
  
 Vous pouvez afficher jusqu’à cinq rapports enregistrés en sélectionnant les rapports dans la zone de liste déroulante **rapport** . Les rapports sont répertoriés selon le horodateur à partir du moment où ils ont été générés.  
  
## <a name="report-format"></a>Format de rapport  
 La visionneuse de rapports affiche les problèmes répertoriés dans trois colonnes. Chaque problème est réductible afin que vous puissiez masquer la description et afficher uniquement les informations importantes.  
  
 La première colonne est la colonne **importance** . Des icônes indiquent l'importance de chaque problème en affichant un cercle rouge avec un X pour signifier des problèmes importants ou entraînant un blocage ou un triangle jaune avec un point d'exclamation pour signifier des problèmes faisant l'objet d'un avertissement ou d'une information. La deuxième colonne, **quand elle est à corriger**, indique quand vous devez résoudre le problème. Vous pouvez trier le rapport en fonction de l' **importance** ou **de la correction de** la colonne. La troisième colonne, **Description**, répertorie le titre du problème.  
  
 Vous pouvez développer un problème pour afficher des informations supplémentaires, un lien vers des informations détaillées à propos de la résolution du problème et un lien pour afficher les détails du problème. Lorsque vous cliquez sur le lien pour obtenir des précisions concernant le problème, une rubrique d'aide s'affiche avec des informations sur le problème et des instructions pour le résoudre. Une fois que vous avez corrigé un problème ou géré vos éléments d’action, vous pouvez marquer les problèmes comme terminés en activant la case à cocher **ce problème a été résolu** . Si vous souhaitez supprimer les problèmes résolus de la liste des problèmes de mise à niveau, cliquez sur **Actualiser**. Le problème ne s’affiche plus tant que vous n’avez pas exécuté l’Assistant analyse du conseiller de mise à niveau sur le même composant, ou appliqué le filtre **problèmes résolus** à partir de l’option **Filtrer par** .  
  
## <a name="report-files"></a>Fichiers de rapport  
 L’Assistant analyse du conseiller de mise à niveau crée des rapports dans le répertoire Mes documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports et crée un sous-répertoire pour chaque serveur que vous analysez. Les fichiers de rapport sont des fichiers XML qui respectent une convention d'affectation de noms spécifique. Lorsque vous lancez la visionneuse de rapports du Conseiller de mise à niveau, les fichiers de rapport dans le répertoire par défaut sont affichés. Lorsque vous copiez des fichiers de rapport dans ce dossier, ceux-ci doivent respecter la convention d'affectation de noms sinon la visionneuse de rapports ne les affiche pas automatiquement.  
  
 Si vous souhaitez partager les informations avec d'autres personnes, vous pouvez leur envoyer le rapport XML. Ou, si vous souhaitez utiliser une autre application, vous pouvez exporter le rapport dans un fichier de valeurs séparées par des virgules (CSV) qui vous permettra de créer une feuille de calcul, un fichier texte ou un message électronique.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : afficher un rapport du conseiller de mise à niveau](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)   
 [Procédure : exporter des rapports](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Comment : filtrer des rapports](../../../2014/sql-server/install/how-to-filter-reports.md)   
 [Résolution des problèmes de mise à niveau](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
