---
title: Rapport d’état du serveur (SSRS en Mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: de8c0b06607ef2a9716229fff7e972c96c916fca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128619"
---
# <a name="report-server-status-ssrs-native-mode"></a>État du serveur de rapports (SSRS en mode natif)
  Utilisez cette page pour afficher les informations sur l'instance du serveur de rapports à laquelle vous êtes connecté. Cette page est la page de démarrage pour la configuration du serveur de rapports. Des pages supplémentaires sont disponibles pour configurer les URL, le compte de service, la base de données du serveur de rapports, la remise des messages électroniques du serveur de rapports, le déploiement avec montée en puissance parallèle et les clés de chiffrement.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 Pour ouvrir la page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], puis connectez-vous à l'instance du serveur de rapports. Pour plus d’informations, consultez [Gestionnaire de Configuration de Reporting Services &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode).  
  
> [!TIP]  
>  Le[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) est installé avec un niveau de privilège « highestAvailable ». Ce comportement est par défaut. Le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a besoin de la communication avec des API WMI [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Une partie de la communication WMI [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requiert un niveau supérieur ou d'administration des privilèges.  
  
 Si vous vous connectez au serveur de rapports et que tous les liens de page sont grisés, vérifiez que le service Report Server est démarré. L' **État du service de rapport :** doit être « Démarré ». Vous pouvez également utiliser l'application de console Services dans les Outils d'administration pour vérifier l'état du service.  
  
## <a name="options"></a>Options  
 **Instance de SQL Server**  
 Affiche les informations sur l'instance du serveur de rapports à laquelle vous êtes connecté. Noms d’instance de serveur de rapports sont basés sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances nommées. L'instance par défaut est MSSQLSERVER. Une instance nommée correspond à une valeur que vous avez spécifiée pendant l'installation. Pour plus d’informations sur les instances, consultez [travailler avec plusieurs Versions et Instances de SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
> [!NOTE]  
>  Dans SQL Server Express with Advanced Services, l'instance par défaut est SQLExpress.  
  
 **ID de l'instance**  
 Correspond à un dossier sur le système de fichiers contenant les fichiers programme de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous êtes connecté. Le **ID d’Instance** valeur est assignée par le programme d’installation dans le format *composant*. *instance*, où *composant* est une valeur qui représente un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composant et *instance* est un nom d’instance. MSSQLSERVER est le nom de l'instance par défaut. Par exemple, si vous installez des instances par défaut de la [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] composants, les noms de dossiers correspondants sont les suivants :  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 Si vous installez une deuxième instance d’un composant que vous avez déjà installé, tel que le [!INCLUDE[ssDE](../../includes/ssde-md.md)], et que vous nommez l’instance Contoso, le **ID d’Instance** est MSSQL12. Contoso.  
  
 **Édition**  
 Affiche les informations sur l'édition. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](http://go.microsoft.com/fwlink/?linkid=232473).  
  
 **Version du produit**  
 Affiche la version de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous avez installé.  
  
 **Base de données du serveur de rapports**  
 Affiche le nom de la base de données du serveur de rapports qui stocke les données d'application pour l'instance du serveur de rapports en cours.  
  
 **Mode de serveur de rapports**  
 La valeur **Natif**doit toujours être affichée. Le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Gestionnaire de configuration prend uniquement en charge les serveurs de rapports en mode natif. Si vous voyez la valeur **Mode intégré SharePoint**, cela peut indiquer que votre déploiement en mode natif n'est pas configuré correctement et que vous devez vous connecter à un catalogue de rapports en mode natif. Utilisez la page **Base de données** du Gestionnaire de configuration pour modifier la base de données et pour créer une base de données ou vous connecter à un catalogue de la base de données du serveur de rapports en mode natif.  
  
 **État du serveur**  
 Indique si le service Report Server est en cours d'exécution.  
  
 **Démarrer**  
 Démarre le service Report Server. Le redémarrage du service est nécessaire après certains changements de configuration (par exemple, lors de la reconfiguration d'un serveur de rapports après un changement du nom de l'ordinateur). Si vous reconfigurez les réservations d'URL, le service redémarrera automatiquement. Le redémarrage est nécessaire pour prendre en compte les modifications.  
  
 **Arrêter**  
 Arrête le service Report Server. L'arrêt du service provoque l'arrêt du serveur de rapports. Pour plus d’informations, consultez [démarrer et arrêter le Service Report Server](../../reporting-services/report-server/start-and-stop-the-report-server-service.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Gestionnaire de Configuration de Reporting Services &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [Initialiser un serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
