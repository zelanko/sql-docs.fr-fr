---
title: 'Comment : exécuter l’Assistant analyse du Conseiller de mise à niveau | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
caps.latest.revision: 36
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 29aeaa20d5fed63731c84872ffb193da4bcfce27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282565"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a>Procédure : exécuter l'Assistant Analyse du Conseiller de mise à niveau
  Vous démarrez l'Assistant Analyse du Conseiller de mise à niveau à partir de la page de démarrage du Conseiller de mise à niveau. Cette rubrique décrit comment exécuter l'Assistant Analyse du Conseiller de mise à niveau.  
  
> [!IMPORTANT]  
>  Lorsque vous exécutez l'Assistant Analyse du Conseiller de mise à niveau, le Conseiller de mise à niveau enregistre les rapports dans le dossier des rapports par défaut. Toutefois, la visionneuse de rapports affiche uniquement les cinq derniers rapports enregistrés. L’emplacement par défaut pour les rapports est Mes Documents\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Advisor\110\Reports mise à niveau.  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a>Pour exécuter l’Assistant analyse du Conseiller de mise à niveau  
  
1.  Dans la page de démarrage Upgrade Advisor, cliquez sur **lancer l’Assistant analyse Conseiller de mise à niveau**.  
  
2.  Sur le  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants** page, entrez le nom du serveur à analyser dans le **nom du serveur** , puis cliquez sur **détecter**. Utilisez les indications suivantes pour le nom du serveur :  
  
    -   Pour analyser les instances non cluster, entrez le nom de l'ordinateur.  
  
    -   Pour analyser les instances cluster, entrez le nom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtuel.  
  
    -   Pour analyser les composants non cluster installés sur un nœud d'un cluster, entrez le nom du nœud.  
  
    > [!WARNING]  
    >  Le Conseiller de mise à niveau ne prend pas en charge la connexion à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui n'est pas définie pour utiliser le port standard (1433) pour les connexions clientes. Si vous voulez vous connecter à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui n'utilise pas le port standard (1433), créez un alias à l'aide de l'adresse IP et du port. Pour plus d’informations sur la configuration des protocoles clients et la création d’un alias pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances, consultez [configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md).  
    >   
    >  Si vous n’avez pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installé sur l’ordinateur sur lequel vous exécutez le Conseiller de mise à niveau, cliquez sur **Démarrer**, puis exécutez `cliconfg`. Cette opération ouvre le  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilitaire réseau Client** boîte de dialogue. Utilisez le **Alias** onglet pour créer l’alias.  
  
3.  Passez en revue la liste des composants détectés, modifiez les sélections si nécessaire, puis cliquez sur **suivant**.  
  
4.  Sur le **paramètres de connexion** , sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous souhaitez analyser, sélectionnez la méthode d’authentification et, si nécessaire, entrez les informations de nom et mot de passe utilisateur, puis cliquez sur **suivant**.  
  
     MSSQLSERVER est le nom de l'instance par défaut.  
  
5.  Pour les composants sélectionnés, entrez les informations demandées. Pour plus d’informations sur les boîtes de dialogue individuelles, consultez [sur l’Interface utilisateur Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
6.  Sur le **paramètre confirmer du Conseiller de mise à niveau** page, passez en revue les informations que vous avez entré. Vous pouvez sélectionner **envoyer des rapports à [!INCLUDE[msCoName](../../includes/msconame-md.md)]**  si vous souhaitez soumettre votre rapport de mise à niveau. Vous pouvez également examiner la politique de confidentialité.  
  
7.  Cliquez sur **exécuter** pour analyser l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
8.  Lorsque l’analyse est terminée, cliquez sur **lancer le rapport** pour afficher les problèmes de mise à niveau détectés.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : lancer le Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Exécutez le Conseiller de mise à niveau &#40;Interface utilisateur&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
