---
title: Base de données (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4fc3fdb873a567bef9326232e5435cea5649b041
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054880"
---
# <a name="database-ssrs-native-mode"></a>Base de données (SSRS en mode natif)
  Utilisez la page Base de données pour créer et configurer les bases de données du serveur de rapports qui fournissent le stockage interne pour une ou plusieurs instances du serveur de rapports. Si vous configurez un serveur de rapports pour utiliser une base de données de serveur de rapports, vous devez utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour créer la base de données.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.  
  
 La création d'une base de données de serveur de rapports et la configuration de la connexion est un processus comportant plusieurs étapes. Pour vous guider à travers les étapes, cette page propose un Assistant pour chaque type de tâche. Les autorisations et les connexions sont créées ou mises à jour automatiquement. Vous pouvez surveiller l'état de chaque étape dans la page Progression. Si une erreur se produit, vous pouvez cliquer sur l'erreur pour obtenir plus d'informations sur sa résolution.  
  
 Une base de données de serveur de rapports doit prendre en charge un mode serveur spécifique. Le mode par défaut est le mode natif, mais vous pouvez également créer une base de données de serveur de rapports en mode intégré SharePoint si vous exécutez un serveur de rapports dans un déploiement plus vaste d'un produit ou d'une technologie SharePoint. Pour plus d’informations, consultez [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et cliquez sur **Base de données** dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Nom de l’SQL Server**  
 Dans la base de données en cours du serveur de rapports, **Nom du serveur SQL** spécifie le nom du [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui exécute la base de données du serveur de rapports. Vous pouvez utiliser une instance par défaut ou nommée sur un ordinateur local ou distant.  
  
 **Database Name**  
 Spécifie le nom de la base de données du serveur de rapports qui stocke les données du serveur.  
  
 **Mode du serveur de rapports**  
 Indique si la base de données de serveur de rapports prend en charge le mode natif ou le mode intégré SharePoint. Pour plus d’informations, consultez [Reporting Services serveur de rapports](../../../2014/reporting-services/reporting-services-report-server.md).  
  
 **Modifier la base de données**  
 Démarrez un Assistant qui vous guide à travers toutes les étapes requises pour créer ou sélectionner une base de données de serveur de rapports.  
  
 **Type d’informations d’identification**  
 Détermine les informations d'identification utilisées par le serveur de rapports pour la connexion à la base de données du serveur de rapports. Les types d'informations d'identification que vous pouvez spécifier incluent le compte de service, un utilisateur de domaine Windows, un utilisateur local Windows ou une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur la sélection des informations d’identification, consultez [configurer une connexion à la base de données du serveur de rapports &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Nom d’utilisateur**  
 Spécifie un compte d'utilisateur du domaine si vous utilisez les informations d'identification Windows ou une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous utilisez les informations d'identification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous utilisez des informations d’identification Windows, spécifiez-les au format suivant : * \<domain> \\<compte \> *.  
  
 **Mot de passe**  
 Spécifie le mot de passe du compte.  
  
 **Modifier les informations d’identification**  
 Démarrez un Assistant qui vous guide à travers toutes les étapes requises pour sélectionner un autre compte ou mettre à jour le mot de passe du compte utilisé pour se connecter à la base de données du serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une base de données du serveur de rapports en mode natif &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Gestionnaire de configuration de Reporting Services les rubriques d’aide F1 &#40;le mode natif SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Base de données du serveur de rapports &#40;le mode natif SSRS&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
