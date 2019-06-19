---
title: Vue d’ensemble du Conseiller de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- SQL Server Upgrade Advisor, components
- tools [Upgrade Advisor]
- Upgrade Advisor [SQL Server], components
- components [Upgrade Advisor]
- Upgrade Advisor Analysis Wizard
- limitations [Upgrade Advisor]
- analyzing system [Upgrade Advisor]
- analyzing system [Upgrade Advisor], about analysis
ms.assetid: f5c56f63-4478-40af-abb9-642f58a0026c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c78630764a26bb8fe281446c1bb997f18d965db7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66091595"
---
# <a name="upgrade-advisor-overview"></a>Vue d'ensemble du Conseiller de mise à niveau
  Le Conseiller de mise à niveau fournit une console centrale pour analyser les composants [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], et pour afficher des rapports contenant des informations sur les résultats de l'analyse.  
  
## <a name="how-upgrade-advisor-works"></a>Fonctionnement du Conseiller de mise à niveau  
 Lorsque vous exécutez le Conseiller de mise à niveau, la page de démarrage du Conseiller de mise à niveau s'affiche. La page de démarrage du Conseiller de mise à niveau correspond au point de lancement des éléments suivants :  
  
-   Assistant Analyse du Conseiller de mise à niveau  
  
-   Visionneuse de rapports du Conseiller de mise à niveau  
  
-   Aide du Conseiller de mise à niveau  
  
 Lorsque vous utilisez le Conseiller de mise à niveau pour la première fois, exécutez l'Assistant Analyse du Conseiller de mise à niveau pour analyser un serveur. Lorsque l’Assistant a terminé l’analyse, cliquez sur **lancer le rapport** à partir de l’Assistant ou retournez à la page de démarrage du Conseiller de mise à niveau. À partir de là, exécutez la visionneuse de rapports du Conseiller de mise à niveau afin d'afficher le rapport. Le rapport fournit des liens vers des informations qui vous aideront à résoudre les problèmes connus.  
  
## <a name="upgrade-advisor-analysis-wizard"></a>Assistant Analyse du Conseiller de mise à niveau  
 Pour effectuer une analyse, cliquez sur **lancer l’Assistant analyse Conseiller de mise à niveau** sur la page de démarrage du Conseiller de mise à niveau. L'Assistant Analyse du Conseiller de mise à niveau rassemble des informations sur l'ordinateur, les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les fichiers de trace que vous souhaitez analyser. Une fois que toutes les informations ont été rassemblées et confirmées, l'Assistant Analyse du Conseiller de mise à niveau analyse les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Chaque fois que vous exécutez l'Assistant Analyse du Conseiller de mise à niveau, un rapport distinct est généré et les rapports existants pour les composants sélectionnés ne sont pas remplacés. Toutefois, la visionneuse de rapports affiche uniquement les cinq derniers rapports.  
  
 Lorsque l'Assistant Analyse du Conseiller de mise à niveau termine son analyse, il crée un fichier XML pour chaque composant que vous avez inclus dans l'analyse. Les fichiers XML contiennent les éléments et les problèmes découverts dans chaque composant.  
  
### <a name="what-upgrade-advisor-analyzes"></a>Objets d'analyse du Conseiller de mise à niveau  
 Un analyseur dédié s'exécute dans le contexte du Conseiller de mise à niveau pour chaque composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La sortie de chaque analyseur correspond à un rapport XML sur ce composant.  
  
 Le Conseiller de mise à niveau interroge les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivants :  
  
-   Serveur de base de données (également connu sous le nom de [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), qui comprend la réplication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, la recherche en texte intégral et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
> [!NOTE]  
>  Pendant l'analyse, chaque analyseur crée un fichier journal. Vous pouvez utiliser ces fichiers journaux pour dépanner l'analyse. Par exemple, si le Conseiller de mise à niveau s'exécute lentement, vous pouvez consulter les fichiers journaux pour déterminer la cause du délai.  
  
### <a name="upgrade-advisor-limitations"></a>Limites du Conseiller de mise à niveau  
 Le Conseiller de mise à niveau ne peut pas détecter tous les problèmes susceptibles d'affecter une mise à niveau. Par exemple, si vous avez incorporé du code SQL dans une application cliente qui s'exécute sur les ordinateurs de bureaux d'utilisateurs finaux, le Conseiller de mise à niveau ne pourra pas analyser les applications. Pour ces éléments, vous devez encore considérer les problèmes et mettre à niveau, migrer ou modifier les informations comme votre installation l'exige.  
  
 Le Conseiller de mise à niveau n'analyse pas les procédures stockées chiffrées, le code dans les procédures stockées étendues ni le code source dans les langages autres que [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="upgrade-advisor-report-viewer"></a>Visionneuse de rapports du Conseiller de mise à niveau  
 Pour afficher un rapport du Conseiller de mise à niveau, cliquez sur **lancer la visionneuse de rapports** sur la page de démarrage du Conseiller de mise à niveau. Lorsque la visionneuse de rapports du Conseiller de mise à niveau démarre, les rapports présents dans le répertoire par défaut sont chargés. Les rapports ne sont pas affichés si la visionneuse de rapports de conseiller de mise à niveau ne trouve pas tous les rapports dans le répertoire par défaut. Si le répertoire par défaut ne contient pas de rapport, vous pouvez exécuter l'Assistant Analyse du Conseiller de mise à niveau pour créer un rapport ou charger un rapport existant à partir d'un autre serveur ou d'un sous-répertoire.  
  
 Le Conseiller de mise à niveau [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne remplace pas les rapports existants. Toutefois, la visionneuse de rapports affiche uniquement les cinq derniers rapports. Pour afficher un rapport antérieur, sélectionnez le rapport dans le **rapport** zone de liste déroulante. Le horodateur indique la date et l'heure auxquelles le rapport a été généré.  
  
 Lorsque des fichiers XML de l'Assistant Analyse du Conseiller de mise à niveau sont chargés dans la visionneuse de rapports du Conseiller de mise à niveau, un rapport est affiché pour chaque composant. Le rapport contient tous les problèmes connus, détectables et indétectables, que vous devez traiter. Chaque problème est accompagné d'une icône qui indique son importance, d'une étiquette qui vous informe quand le problème doit être résolu et d'une courte description. Lorsque vous développez un problème, une description plus longue apparaît, ainsi qu'un lien vers les détails du problème et un lien vers le fichier d'aide. Pour chaque problème, les informations fournies doivent être suffisantes pour vous permettre de résoudre le problème.  
  
 La plupart des composants ont des problèmes qui ne peuvent pas être détectés. Pour afficher ces problèmes, développez le **autres problèmes de mise à niveau** pour le composant d’élément, puis cliquez sur le lien pour afficher des informations supplémentaires sur les problèmes dans la documentation. Pour plus d'informations sur les problèmes de compatibilité descendante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
