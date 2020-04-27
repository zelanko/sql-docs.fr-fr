---
title: 'Procédure : installer le conseiller de mise à niveau | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
ms.openlocfilehash: 0de86b9690f0647803938218ce566508662da20e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094923"
---
# <a name="how-to-install-upgrade-advisor"></a>Procédure : installer le Conseiller de mise à niveau
  Le Conseiller de mise à niveau prend en charge l'analyse distante de tous les composants pris en charge, à l'exception de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si vous n'analysez pas d'instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez installer le Conseiller de mise à niveau sur n'importe quel ordinateur pouvant se connecter à vos instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les composants requis du Conseiller de mise à niveau doivent également être installés sur l'ordinateur. Si vous analysez des instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez installer le Conseiller de mise à niveau sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [installation du conseiller de mise à niveau](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
### <a name="to-install-upgrade-advisor"></a>Pour installer le Conseiller de mise à niveau  
  
1.  Démarrez l'installation en appliquant l'une des méthodes suivantes :  
  
    -   Si vous effectuez l’installation à [!INCLUDE[msCoName](../../includes/msconame-md.md)] partir du site Web, cliquez sur le lien de **Téléchargement** , puis cliquez sur le bouton **exécuter** pour démarrer l’installation.  
  
    -   Si vous effectuez l’installation à partir du support du produit, ouvrez le dossier **Redist** , ouvrez le dossier du **conseiller de mise à niveau** , puis double-cliquez sur **SQLUA. msi**.  
  
    > [!NOTE]  
    >  Le Conseiller de mise à niveau nécessite [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4. S'il n'est pas installé, ou si vous disposez d'une version préliminaire, un message d'erreur s'affiche. Désinstallez toute version antérieure du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], puis installez la version la plus récente de .NET Framework 4.  
    >   
    >  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom est un composant requis pour l' [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation du conseiller de mise à niveau et n’est pas installé par le programme d’installation du conseiller de mise à niveau. Le programme d’installation vous demande de télécharger et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] d’installer le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ScriptDom à partir du Feature Pack.  
  
2.  Sur la page **Bienvenue dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] le programme d’installation du conseiller de mise à niveau** , cliquez sur **suivant**.  
  
3.  Sur la page **contrat de licence** , lisez le contrat de licence. Si vous acceptez, sélectionnez **J’accepte le contrat de licence** , puis cliquez sur **suivant**.  
  
4.  Dans la page **informations d’inscription** , entrez votre nom et votre société.  
  
5.  Dans la page **sélection de fonctionnalités** , examinez la valeur **chemin d’installation** . Si nécessaire, utilisez le bouton **Parcourir** pour modifier l’emplacement. Cliquez sur **Suivant**.  
  
6.  Dans la page **prêt à installer le programme** , cliquez sur **installer** pour installer le conseiller de mise à niveau.  
  
7.  Cliquez sur **Terminer** pour quitter l'Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration requise par le Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
