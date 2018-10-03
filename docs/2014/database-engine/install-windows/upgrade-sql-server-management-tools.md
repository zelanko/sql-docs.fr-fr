---
title: Mettre à jour les outils d’administration SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- management tools, upgrading
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6ecfb2355272ac511e8ccf440f759d01f30f31cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226259"
---
# <a name="upgrade-sql-server-management-tools"></a>Mettre à jour les outils d'administration SQL Server
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge la mise à niveau à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. Cette rubrique documente la prise en charge et le fonctionnement de la mise à niveau des Outils d'administration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des composants de gestion tels que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, la Messagerie de base de données, les Plans de Maintenance, XPStar et XPWeb.  
  
> [!IMPORTANT]  
>  Dans le cas d'une installation locale, vous devez exécuter le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en qualité d'administrateur. Si vous exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine doté des autorisations de lecture et d'exécution sur le partage distant.  
  
## <a name="known-upgrade-issues"></a>Problèmes de mise à niveau connus  
 Considérez les points suivants avant de procéder à une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
### <a name="for-all-upgrade-scenarios"></a>Pour tous les scénarios de mise à niveau :  
  
-   Tous les serveurs TSX doivent être mis à niveau avant que le serveur MSX ne le soit. Pour plus d’informations sur MSX/TSX dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Administration automatisée à l’échelle d’une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md).  
  
-   Tous les composants d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être mis à niveau simultanément. Les numéros de version des composants [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] doivent être identiques dans une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Vous pouvez ajouter des composants à une installation existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en même temps que vous procédez à une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [mise à niveau vers SQL Server 2014 avec l’Assistant Installation &#40;le programme d’installation&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les Outils clients, tels que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , sqlcmd et osql, ne sont pas mis à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. À la place, les outils clients s'exécutent côte à côte avec les outils des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge l’importation des paramètres à partir des versions antérieures des Outils clients [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   L'authentification depuis l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est mise à jour depuis l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers l'authentification Windows pendant la mise à niveau. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] L’authentification n’est pas prise en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Les données des travaux et des alertes sont conservées pendant la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Si SQLMail est utilisé dans l'instance à mettre à niveau, les composants XPs associés sont pris en charge et activés après la mise à niveau. Sinon, ils sont désactivés.  
  
-   La messagerie de base de données, également appelée SQLiMail, est mise à niveau avec le composant [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Par défaut, la messagerie sera désactivée après la mise à niveau. Toutes les mises à jour de schéma doivent être harmonisées avec un script de mise à jour après la mise à niveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Mises à niveau de la version et de l'édition prises en charge](supported-version-and-edition-upgrades.md)   
 [Compatibilité descendante](../../getting-started/backward-compatibility.md)   
 [Mise à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation &#40;le programme d’installation&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
