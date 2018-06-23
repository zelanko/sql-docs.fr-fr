---
title: URL du Gestionnaire de rapports (SSRS en Mode natif) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 1469d877b992638119ad60bafadc1023a4ed5fc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041942"
---
# <a name="report-manager-url-ssrs-native-mode"></a>URL du gestionnaire de rapports (SSRS en mode natif)
  Utilisez la page URL du Gestionnaire de rapports pour configurer ou modifier l'URL permettant d'accéder au Gestionnaire de rapports. Par défaut, l'URL du Gestionnaire de rapports hérite du préfixe, de l'adresse IP et du port de l'URL du service Web Report Server URL. La raison en est que le Gestionnaire de rapports fournit l'accès frontal au service Web qui s'exécute au sein du même service Report Server. Si vous isolez les applications de service et utilisez le Gestionnaire de rapports pour accéder à un service Web Report Server sur un autre ordinateur, vous devez modifier le fichier RSReportServer.config pour pointer le Gestionnaire de rapports sur une instance différente. Pour plus d’informations sur la configuration d’une connexion de gestionnaire de rapports à un serveur de rapports distant, consultez [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 Si vous êtes en train de configurer le serveur de rapports pour qu'il s'exécute en mode intégré SharePoint, ne créez pas l'URL du Gestionnaire de rapports. Le Gestionnaire de rapports n'est pas pris en charge sur un serveur de rapports exécuté en mode intégré SharePoint. Si une URL existe déjà pour le Gestionnaire de rapports, elle devient indisponible après que vous avez configuré le serveur de rapports pour qu'il s'exécute en mode intégré SharePoint.  
  
 Pour ouvrir cette page, démarrez le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager et cliquez sur **URL du Gestionnaire de rapports** dans le volet de navigation. Pour plus d’informations sur la façon de démarrer le Gestionnaire de Configuration, consultez [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!NOTE]  
>  Si le Gestionnaire de rapports n'est pas activé, vous ne pouvez pas définir d'options sur cette page. Pour plus d’informations sur l’activation du Gestionnaire de rapports, consultez [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Répertoire virtuel**  
 Spécifie le nom de répertoire virtuel pour le Gestionnaire de rapports. Vous ne pouvez avoir qu'un seul nom de répertoire virtuel pour chaque instance du Gestionnaire de rapports sur le même ordinateur.  
  
 **URL**  
 Affiche l'URL définie pour l'instance en cours du Gestionnaire de rapports.  
  
 **Avancé**  
 Ajoutez une URL supplémentaire pour l'instance en cours du Gestionnaire de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [URL des fichiers de Configuration de &#40;Gestionnaire de Configuration de SSRS&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  