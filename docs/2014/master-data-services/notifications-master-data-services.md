---
title: Notifications (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 54f8cdc55322144414be11dd837bd723b4ed3c10
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65478968"
---
# <a name="notifications-master-data-services"></a>Notifications (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] peut être configuré pour envoyer une notification par e-mail en cas d’échec de validation de règle métier ou l’état d’une version de modèle change.  
  
## <a name="how-notifications-are-sent"></a>Mode d'envoi des notifications  
 Vous pouvez configurer les notifications dans [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Les notifications envoient des messages électroniques à l’aide de la messagerie de base de données sur l’instance du [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] qui héberge la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations sur la messagerie de base de données, consultez [Objets de configuration de la messagerie de base de données](../relational-databases/database-mail/database-mail-configuration-objects.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="when-notifications-are-sent"></a>Critères d'envoi des notifications  
 Une fois les notifications configurées, elles peuvent être envoyées automatiquement par courrier électronique dans les cas suivants.  
  
|Instance|Description|  
|--------------|-----------------|  
|Les données ne remplissent pas les conditions de validation des règles d'entreprise.|Les règles d'entreprise doivent être configurées individuellement pour envoyer des messages électroniques lorsqu'une valeur d'attribut fait échouer la validation de la règle d'entreprise. Pour plus d’informations, consultez [Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md).|  
|L'état d'une version de modèle change|Chaque fois que l'état d'une version de modèle change, les utilisateurs qui sont des administrateurs de modèle reçoivent automatiquement des notifications. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).|  
  
## <a name="system-settings"></a>Paramètres système  
 Il existe des paramètres dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] qui affectent les notifications. Vous pouvez ajuster ces paramètres dans [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] ou directement dans la table Paramètres système dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Configurer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour envoyer des notifications par courrier électronique.|[Configurer des notifications par courrier électronique &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|Configurer [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour envoyer des notifications lorsque les valeurs d'attribut changent.|[Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [Résolution des problèmes liés aux notifications par courrier électronique (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
