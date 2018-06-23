---
title: Base de données (SSRS en Mode natif) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 4c8ff22e9edee8af2af4b948289b56c3078e4232
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043313"
---
# <a name="database-ssrs-native-mode"></a>Base de données (SSRS en mode natif)
  Utilisez la page Base de données pour créer et configurer les bases de données du serveur de rapports qui fournissent le stockage interne pour une ou plusieurs instances du serveur de rapports. Si vous configurez un serveur de rapports pour utiliser une base de données du serveur de rapports distant, vous devez utiliser le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager pour créer la base de données.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 La création d'une base de données de serveur de rapports et la configuration de la connexion est un processus comportant plusieurs étapes. Pour vous guider à travers les étapes, cette page propose un Assistant pour chaque type de tâche. Les autorisations et les connexions sont créées ou mises à jour automatiquement. Vous pouvez surveiller l'état de chaque étape dans la page Progression. Si une erreur se produit, vous pouvez cliquer sur l'erreur pour obtenir plus d'informations sur sa résolution.  
  
 Une base de données de serveur de rapports doit prendre en charge un mode serveur spécifique. Le mode par défaut est le mode natif, mais vous pouvez également créer une base de données de serveur de rapports en mode intégré SharePoint si vous exécutez un serveur de rapports dans un déploiement plus vaste d'un produit ou d'une technologie SharePoint. Pour plus d’informations, consultez [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Pour ouvrir cette page, démarrez le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager et cliquez sur **base de données** dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Nom du serveur SQL**  
 Dans la base de données en cours, **nom SQL Server** Spécifie le nom de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui exécute la base de données du serveur de rapports. Vous pouvez utiliser une instance par défaut ou nommée sur un ordinateur local ou distant.  
  
 **Database Name**  
 Spécifie le nom de la base de données du serveur de rapports qui stocke les données du serveur.  
  
 **Mode de serveur de rapports**  
 Indique si la base de données de serveur de rapports prend en charge le mode natif ou le mode intégré SharePoint. Pour plus d’informations, consultez [Reporting Services Report Server](../../../2014/reporting-services/reporting-services-report-server.md).  
  
 **Base de données modifiées**  
 Démarrez un Assistant qui vous guide à travers toutes les étapes requises pour créer ou sélectionner une base de données de serveur de rapports.  
  
 **Type d’informations d’identification**  
 Détermine les informations d'identification utilisées par le serveur de rapports pour la connexion à la base de données du serveur de rapports. Les types d’informations d’identification que vous pouvez spécifier incluent le compte de service, un utilisateur de domaine Windows, l’utilisateur Windows local, ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion de base de données. Pour plus d’informations sur la sélection des informations d’identification, consultez [configurer une connexion de base de données de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Nom d'utilisateur**  
 Spécifie un compte d’utilisateur de domaine si vous utilisez des informations d’identification Windows, ou un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informations d’identification. Si vous utilisez des informations d’identification Windows, indiquez-les dans ce format :  *\<domaine >\\< compte\>*.  
  
 **Mot de passe**  
 Spécifie le mot de passe du compte.  
  
 **Modifier les informations d’identification**  
 Démarrez un Assistant qui vous guide à travers toutes les étapes requises pour sélectionner un autre compte ou mettre à jour le mot de passe du compte utilisé pour se connecter à la base de données du serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Base de données du serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Configurer une connexion de base de données de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  