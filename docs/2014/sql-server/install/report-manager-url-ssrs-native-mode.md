---
title: URL de Gestionnaire de rapports (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: dd4ff661a10eca71781aee9d1886e80936f6246d
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952412"
---
# <a name="report-manager-url-ssrs-native-mode"></a>URL du gestionnaire de rapports (SSRS en mode natif)
  Utilisez la page URL du Gestionnaire de rapports pour configurer ou modifier l'URL permettant d'accéder au Gestionnaire de rapports. Par défaut, l'URL du Gestionnaire de rapports hérite du préfixe, de l'adresse IP et du port de l'URL du service Web Report Server URL. La raison en est que le Gestionnaire de rapports fournit l'accès frontal au service Web qui s'exécute au sein du même service Report Server. Si vous isolez les applications de service et utilisez le Gestionnaire de rapports pour accéder à un service Web Report Server sur un autre ordinateur, vous devez modifier le fichier RSReportServer.config pour pointer le Gestionnaire de rapports sur une instance différente. Pour plus d’informations sur la configuration d’une connexion Gestionnaire de rapports à un serveur de rapports distant, consultez [ &#40;gestionnaire de configuration de Reporting Services mode&#41;natif](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 Si vous êtes en train de configurer le serveur de rapports pour qu'il s'exécute en mode intégré SharePoint, ne créez pas l'URL du Gestionnaire de rapports. Le Gestionnaire de rapports n'est pas pris en charge sur un serveur de rapports exécuté en mode intégré SharePoint. Si une URL existe déjà pour le Gestionnaire de rapports, elle devient indisponible après que vous avez configuré le serveur de rapports pour qu'il s'exécute en mode intégré SharePoint.  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et cliquez sur **URL du Gestionnaire de rapports** dans le volet de navigation. Pour plus d’informations sur le démarrage du Configuration Manager, consultez [Gestionnaire de configuration de Reporting Services &#40;mode&#41;natif](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!NOTE]  
>  Si le Gestionnaire de rapports n'est pas activé, vous ne pouvez pas définir d'options sur cette page. Pour plus d’informations sur l’activation d’Gestionnaire de rapports, consultez [ &#40;gestionnaire de configuration de Reporting Services mode&#41;natif](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Répertoire virtuel**  
 Spécifie le nom de répertoire virtuel pour le Gestionnaire de rapports. Vous ne pouvez avoir qu'un seul nom de répertoire virtuel pour chaque instance du Gestionnaire de rapports sur le même ordinateur.  
  
 **URL**  
 Affiche l'URL définie pour l'instance en cours du Gestionnaire de rapports.  
  
 **Avancé**  
 Ajoutez une URL supplémentaire pour l'instance en cours du Gestionnaire de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [URL dans les fichiers &#40;de configuration&#41; Configuration Manager SSRS](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
