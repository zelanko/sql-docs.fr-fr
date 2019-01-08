---
title: Utilisez le Conseiller de mise à niveau pour préparer des mises à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server]
- upgrading SQL Server, Upgrade Advisor
- upgrading SQL Server, preparing to upgrade
- SQL Server Upgrade Advisor
- analyzing installations for upgrading [SQL Server]
ms.assetid: d85b0833-ddeb-42e3-9397-97ea60d521b7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8b12b22af124250fe05baab5d08a6585de061b56
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368071"
---
# <a name="use-upgrade-advisor-to-prepare-for-upgrades"></a>Utiliser le Conseiller de mise à niveau pour la préparation des mises à niveau
  Le Conseiller de mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous assiste lors de la préparation des mises à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Le Conseiller de mise à niveau analyse les composants installés des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis génère un rapport qui identifie les problèmes à résoudre avant ou après la mise à niveau.  
  
## <a name="how-upgrade-advisor-works"></a>Fonctionnement du Conseiller de mise à niveau  
 Lorsque vous exécutez le Conseiller de mise à niveau, la page d'accueil du Conseiller de mise à niveau s'affiche. À partir de la page d'accueil, vous pouvez exécuter les outils suivants :  
  
-   Assistant Analyse du Conseiller de mise à niveau  
  
-   Visionneuse de rapports du Conseiller de mise à niveau  
  
-   Aide du Conseiller de mise à niveau  
  
 À la première utilisation du Conseiller de mise à niveau, exécutez l'Assistant Analyse du Conseiller de mise à niveau pour analyser les composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque l'Assistant a terminé l'analyse, affichez les rapports obtenus dans la visionneuse de rapports du Conseiller de mise à niveau. Chaque rapport inclut des liens vers des informations de l'aide du Conseiller de mise à niveau qui vous permettront de corriger problèmes connus ou de minimiser leur incidence.  
  
## <a name="upgrade-advisor-analysis"></a>Analyse du Conseiller de mise à niveau  
 Le Conseiller de mise à niveau analyse les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivants :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
 L'analyse examine les objets accessibles (tels que les scripts, les procédures stockées, les déclencheurs et les fichiers de trace). Le Conseiller de mise à niveau ne peut pas analyser les logiciels applicatifs ni les procédures stockées chiffrées.  
  
 La sortie se présente sous la forme d'un rapport XML. Pour afficher le rapport XML, utilisez la visionneuse de rapports du Conseiller de mise à niveau.  
  
> [!NOTE]  
>  Les rapports peuvent contenir un élément « autres problèmes de mise à niveau ». Cet élément mène à une liste de problèmes qui ne sont pas détectés par le Conseiller de mise à niveau, mais qui peuvent exister sur votre serveur ou dans vos applications. Vous devez examiner la liste des problèmes non détectables et déterminer si vous devez modifier votre serveur ou vos applications en raison des problèmes non détectables.  
  
## <a name="how-to-install-and-run-upgrade-advisor"></a>Comment installer et exécuter le Conseiller de mise à niveau  
 L'emplacement d'installation du Conseiller de mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dépend des éléments que vous allez analyser. Le Conseiller de mise à niveau prend en charge l'analyse distante de tous les composants pris en charge, à l'exception de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si vous n'analysez pas d'instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez installer le Conseiller de mise à niveau sur n'importe quel ordinateur pouvant se connecter à votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et répondant à la configuration requise du Conseiller de mise à niveau. Pour plus d’informations, consultez [Mises à niveau de la version et de l’édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md). Si vous analysez des instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez installer le Conseiller de mise à niveau sur le serveur de rapports.  
  
 Le Conseiller de mise à niveau est disponible dans un Feature Pack.  
  
 Conditions préalables pour installer et exécuter le Conseiller de mise à niveau sont les suivantes :  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2, Windows 7 SP1, et [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.  
  
-   Windows Installer depuis la version 4.5. Vous pouvez installer le programme d’installation de Windows à partir de la [site Web du programme d’installation Windows](https://go.microsoft.com/fwlink/?LinkId=49112).  
  
-   Microsoft .NET Framework 4. .NET framework 4 est disponible sur le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support du produit et à partir de la [page de téléchargement de .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=209895).  
  
    -   Pour installer .NET Framework 4 à partir du support de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], localisez la racine du lecteur de disque. Ensuite, double-cliquez sur le dossier \redist, sur le dossier DotNetFrameworks et exécutez dotNetFx40_Full_x86_x64.exe (pour les systèmes d'exploitation 32 bits ou 64 bits).  
  
 Pour installer le Conseiller de mise à niveau à partir du Web, cliquez sur le bouton Télécharger figurant sur la page de téléchargement. Vous pouvez alors soit exécuter l'installation immédiatement, soit enregistrer le fichier SQLUA.msi afin de l'exécuter ultérieurement. Si vous installez à partir du disque du produit, exécutez sqlua.msi directement à partir du disque du produit.  
  
 Une fois que vous installez le Conseiller de mise à niveau, vous pouvez l’ouvrir à partir de la **Démarrer** menu :  
  
-   Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], puis cliquez sur  **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.  
  
 Pour plus d'informations, consultez la documentation relative au Conseiller de mise à niveau incluse dans le téléchargement du Conseiller de mise à niveau, ainsi que les Notes de publication de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec plusieurs Versions et Instances de SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)   
 [Mises à niveau de la version et de l'édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Compatibilité descendante](../../../2014/getting-started/backward-compatibility.md)  
  
  
