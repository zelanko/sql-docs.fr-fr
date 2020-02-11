---
title: Fournisseur WMI pour les classes et propriétés d'événements serveur
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 08b18a3a5805b37a371d6fa17850584d6f4953fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74164909"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>Fournisseur WMI pour les classes et propriétés d'événements serveur
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Les événements serveur suivants composent le modèle de programmation du fournisseur WMI pour les événements serveur. Deux catégories principales d'événements peuvent être interrogées en émettant des requêtes WQL sur le fournisseur. Il s'agit des événements DDL (Data Definition Language) et des événements de trace. Les événements de Service Broker QUEUE_ACTIVATION et BROKER_QUEUE_DISABLED peuvent également être interrogés. Notez la nature inclusive des arborescences suivantes. L'événement DDL_ASSEMBLY_EVENTS, par exemple, inclut tout événement ALTER_ASSEMBLY, CREATE_ASSEMBLY et DROP_ASSEMBLY. De la même façon, l'événement TRC_FULL_TEXT inclut tout événement FT_CRAWL_ABORTED, FT_CRAWL_STARTED et FT_CRAWL_STOPPED. ALL_EVENTS couvre tous les événements DDL, événements de trace, QUEUE_ACTIVATION et BROKER_QUEUE_DISABLED.  
  
 Pour savoir quelles propriétés d'un événement ou d'un groupe d'événements peuvent être interrogées, reportez-vous au schéma d'événement. Par défaut, le schéma d'événement est installé dans le répertoire suivant : [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events .xsd.  
  
 Vous pouvez également vous référer au schéma d’événement publié à [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100)l’adresse.  
  
 Par exemple, en faisant référence à l’événement ALTER_DATABASE, vous allez apprendre que son événement parent est DDL_SERVER_LEVEL_EVENTS et que ses propriétés sont **TSQLCommand** et **DatabaseName**. L’événement hérite également des propriétés **SqlInstance**, **PostTime**, **ComputerName**, **SPID**et **LoginName**. Il ne possède pas d'événements enfants.  
  
> [!NOTE]  
>  Les procédures stockées système qui exécutent des opérations de type DDL peuvent également déclencher des notifications d'événements. Testez vos notifications d'événements pour déterminer leur réponse aux procédures stockées du système qui sont exécutées. Par exemple, l’instruction CREATe TYPE et la procédure stockée **sp_addtype** déclenchent toutes deux une notification d’événement qui est créée sur un événement CREATE_TYPE. Pour plus d’informations, consultez [événements DDL](../../relational-databases/triggers/ddl-events.md).  
  
 **Événements et groupes d'événements DDL (Data Definition Language)**  
  
 ![Fournisseur WMI pour l'arborescence d'événements de serveur](../../relational-databases/wmi-provider-server-events/media/sql-wmi-ddl-events-ktm.gif "Fournisseur WMI pour l'arborescence d'événements de serveur")  
  
 **Événements de trace et groupes d’événements**  
  
 ![Événements et groupes d'événements de trace](../../relational-databases/wmi-provider-server-events/media/sql-wmi-trc-all-events.gif "Événements et groupes d'événements de trace")  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur WMI pour les concepts des événements de serveur](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [Utilisation de WQL avec le fournisseur WMI pour les événements de serveur](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
