---
title: Créer une base de données du serveur de rapports (Gestionnaire de configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- report server database
- databases [Reporting Services], creating
ms.assetid: 8a3a6ffe-4001-46be-8548-94532550f6a5
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 638f96285f4dab2bb109353d7d648b9de8b6bb67
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952300"
---
# <a name="create-a-report-server-database--ssrs-configuration-manager"></a>Créer une base de données du serveur de rapports (Gestionnaire de configuration de SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Le **mode natif** utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deux bases de données relationnelles pour stocker les métadonnées et les objets du serveur de rapports. Une base de données est utilisée pour le stockage principal et l'autre pour le stockage des données temporaires. Les bases de données sont créées ensemble et liées par le nom. Avec une instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les bases de données sont nommées `reportserver` et `reportservertempdb`. Les deux bases de données sont collectivement appelées « base de données de serveur de rapports » ou « catalogue du serveur de rapports ».  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Le **mode SharePoint** comprend une troisième base de données qui est utilisée pour les métadonnées d’alerte de données. Les trois bases de données sont créées pour chaque application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Par ailleurs, les noms de bases de données incluent par défaut un GUID qui représente l'application de service. Voici des exemples de noms des trois bases de données en mode SharePoint :  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370TempDB  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370_Alerting  
  
> [!IMPORTANT]  
>  N'écrivez pas d'applications qui exécutent des requêtes sur la base de données du serveur de rapports. La base de données du serveur de rapports n'est pas un schéma public. La structure des tables peut changer d'une version à la suivante. Si vous écrivez une application qui nécessite un accès à la base de données du serveur de rapports, utilisez toujours les API [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour accéder à la base de données du serveur de rapports.  
>   
>  Les vues du journal des exécutions constituent une exception à cette règle. Pour plus d’informations, consultez [Journal d’exécution du serveur de rapports et vue ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md) .  
  
## <a name="ways-to-create-the-report-server-database"></a>Méthodes pour créer la base de données de serveur de rapports  
 **Mode natif :** vous pouvez créer la base de données du serveur de rapports en mode natif en procédant comme suit :  
  
-   Automatiquement : utilisez l'Assistant Installation de SQL Server, si vous choisissez l'option d'installation de la configuration par défaut. Dans l’Assistant Installation de SQL Server, localisez **Installer et configurer** dans la page d’options d’installation du serveur de rapports. Si vous avez choisi l’option **Installer uniquement** , vous devez utiliser le Gestionnaire de configuration Reporting Services pour créer la base de données.  
  
-   Manuellement : utilisez le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Vous devez créer la base de données du serveur de rapports manuellement si vous utilisez un [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] distant pour héberger la base de données. Pour plus d’informations, consultez [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 **Mode SharePoint :** la page d’options d’installation du serveur de rapports n’offre que l’option **Installer uniquement**pour le mode SharePoint. Cette option installe tous les fichiers [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ainsi que le service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . L'étape suivante consiste à créer au moins une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de l'une des manières suivantes :  
  
-   Utilisez l'Administration centrale de SharePoint pour créer une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez la section « application de service » de l' [étape 3 : créer une application de service Reporting Services](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_create_serrviceapplication).  
  
-   Utilisez les applets de commande PowerShell [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour créer une application de service et les bases de données du serveur de rapports. Pour plus d’informations, consultez l’exemple pour la création d’applications de service dans la rubrique [Applets de commande PowerShell pour le mode SharePoint de Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
## <a name="database-server-version-requirements"></a>Conditions requises pour une version du serveur de bases de données  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est utilisé pour héberger les bases de données du serveur de rapports. L'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] peut être soit locale, soit distante. Voici les versions prises en charge du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui permettent d'héberger les bases de données du serveur de rapports :  
  
- SQL Server 2014
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
 Pour créer la base de données du serveur de rapports sur un ordinateur distant, vous devez configurer la connexion de manière à employer un compte d'utilisateur de domaine ou un compte de service pouvant accéder au réseau. Si vous décidez d'utiliser une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distante, réfléchissez avec soin aux informations d'identification que le serveur de rapports devra utiliser pour se connecter à l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
> [!IMPORTANT]  
>  Le serveur de rapports et l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hébergeant la base de données du serveur de rapports peuvent appartenir à des domaines différents. Dans le cadre d'un déploiement Internet, il est courant d'utiliser un serveur situé derrière un pare-feu. Si vous configurez un serveur de rapports de manière à accéder à Internet, utilisez les informations d'identification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vous connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] située derrière le pare-feu et recourez à IPSEC pour sécuriser la connexion.  
  
## <a name="database-server-edition-requirements"></a>Conditions requises pour une édition du serveur de bases de données  
 Lors de la création d’une base de données de serveur de rapports, soyez conscient que certaines éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peuvent pas être utilisées pour héberger la base de données. Pour plus d’informations, consultez la section « Spécifications de l’édition du serveur de base de données du serveur de rapports » [dans fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services &#40;del&#41;](https://docs.microsoft.com/sql/sql-server/install/reporting-services-configuration-manager-native-mode)  
  
  
