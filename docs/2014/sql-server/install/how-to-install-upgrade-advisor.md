---
title: 'Comment : installer le Conseiller de mise à niveau | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69d5be9a4514f002ebd8c9b7ffb05c6f614e2129
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112925"
---
# <a name="how-to-install-upgrade-advisor"></a>Procédure : installer le Conseiller de mise à niveau
  Le Conseiller de mise à niveau prend en charge l'analyse distante de tous les composants pris en charge, à l'exception de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si vous n'analysez pas d'instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez installer le Conseiller de mise à niveau sur n'importe quel ordinateur pouvant se connecter à vos instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les composants requis du Conseiller de mise à niveau doivent également être installés sur l'ordinateur. Si vous analysez des instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez installer le Conseiller de mise à niveau sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
### <a name="to-install-upgrade-advisor"></a>Pour installer le Conseiller de mise à niveau  
  
1.  Démarrez l'installation en appliquant l'une des méthodes suivantes :  
  
    -   Si vous installez à partir de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] site Web, cliquez sur le **télécharger** lier, puis cliquez sur le **exécuter** bouton pour démarrer l’installation.  
  
    -   Si vous installez à partir du support produit, ouvrez le **redist** dossier, ouvrez le **Upgrade Advisor** dossier, puis double-cliquez sur **sqlua.msi**.  
  
    > [!NOTE]  
    >  Le Conseiller de mise à niveau nécessite [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4. S'il n'est pas installé, ou si vous disposez d'une version préliminaire, un message d'erreur s'affiche. Désinstallez toute version antérieure du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], puis installez la version la plus récente de .NET Framework 4.  
    >   
    >  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom est requis pour l’installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Conseiller de mise à niveau et n’est pas installé par l’installation du Conseiller de mise à niveau. Le programme d’installation vous oblige à télécharger et installer le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom à partir de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.  
  
2.  Sur le **Bienvenue dans le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation du Conseiller de mise à niveau** , cliquez sur **suivant**.  
  
3.  Sur le **contrat de licence** page, lisez le contrat de licence. Si vous acceptez, cochez **J’accepte le contrat de licence** puis cliquez sur **suivant**.  
  
4.  Sur le **informations d’inscription** , entrez votre nom et la société.  
  
5.  Sur le **sélection des fonctionnalités** page, passez en revue la **chemin d’Installation** valeur. Si nécessaire, utilisez le **Parcourir** bouton pour modifier l’emplacement. Cliquez sur **Suivant**.  
  
6.  Sur le **prêt à installer le programme** , cliquez sur **installer** pour installer le Conseiller de mise à niveau.  
  
7.  Cliquez sur **Terminer** pour quitter l'Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Prérequis pour le Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
