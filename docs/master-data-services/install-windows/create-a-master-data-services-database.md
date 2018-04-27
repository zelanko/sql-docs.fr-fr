---
title: Créer une base de données Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: install-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f8ac7845269c9200918266ccd2ae0ccd23c6a14b
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-master-data-services-database"></a>Créer une base de données Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Créez une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] lorsque vous avez besoin d’une nouvelle base de données pour prendre en charge l’application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] et le service web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   Pour plus d’informations sur la configuration requise pour l’ordinateur qui héberge la base de données, consultez [Configuration requise pour la base de données &#40;Master Data Services&#41;](../../master-data-services/install-windows/database-requirements-master-data-services.md).  
  
### <a name="to-create-a-master-data-services-database"></a>Pour créer une base de données Master Data Services  
  
1.  Ouvrez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Dans le volet gauche, cliquez sur **Configuration de la base de données**.  
  
3.  Dans la page **Configuration de la base de données** , cliquez sur **Créer une base de données**.  
  
4.  Exécutez l’Assistant **Création d’une base de données** pour créer et configurer la base de données. Pour plus d’informations sur les options d’interface utilisateur de l’Assistant, consultez [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/create-database-wizard-master-data-services-configuration-manager.md) (Assistant Création d’une base de données (Gestionnaire de configuration de Master Data Services)).  
  
## <a name="next-steps"></a>Next Steps  
  
-   Configurez les paramètres système pour la base de données et l'application Web. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../../master-data-services/system-settings-master-data-services.md).  
  
-   Créez une application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à associer à cette base de données. Pour plus d’informations, consultez [Créer une application web Master Data Manager &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
-   Configurez un plan de maintenance pour sauvegarder la base de données et les journaux des transactions. Pour plus d’informations, consultez [Configuration requise pour la base de données &#40;Master Data Services&#41;](../../master-data-services/install-windows/database-requirements-master-data-services.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
