---
title: Présentation du fournisseur WMI pour les événements serveur
description: Découvrez comment le fournisseur WMI pour les événements de serveur utilise Windows Management Instrumentation pour surveiller les événements en transformant SQL Server en objet WMI géré.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: df2e36110a9e4a52a3587644b96994bc040442e8
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89519776"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a>Présentation du fournisseur WMI pour les événements serveur
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Le fournisseur WMI pour les événements de serveur vous permet d'utiliser WMI (Windows Management Instrumentation) pour surveiller les événements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ce fournisseur fonctionne en transformant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un objet WMI managé. Tout événement qui peut générer une notification d'événements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut tirer parti de WMI via ce fournisseur. En outre, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en tant qu'application de gestion qui interagit avec WMI, peut répondre à ces événements, ce qui augmente l'étendue des événements traités par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par rapport aux versions antérieures.  
  
 Les applications de gestion telles que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent accéder aux événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via le fournisseur WMI pour les événements serveur en publiant des instructions WQL (WMI Query Language). Le langage WQL est un sous-ensemble simplifié du langage SQL, avec quelques extensions spécifiques à WMI. À l'aide du langage WQL, une application récupère un type d'événement à partir d'une base de données ou d'un objet de base de données spécifique. Le fournisseur WMI pour les événements serveur traduit la requête en une notification d'événements, ce qui entraîne la création effective d'une notification d'événements dans la base de données cible. Pour plus d’informations sur le fonctionnement des notifications d’événements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [fournisseur WMI pour les concepts des événements de serveur](https://technet.microsoft.com/library/ms180560.aspx). Les événements qui peuvent être interrogés sont répertoriés dans [fournisseur WMI pour les classes et les propriétés d’événements de serveur](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).  
  
 Lorsqu’un événement qui déclenche la notification d’événement pour envoyer un message se produit, le message est envoyé à un service cible prédéfini dans **msdb** , nommé **SQL/Notifications/ProcessWMIEventProviderNotification/v 1.0**. Le service place l’événement dans une file d’attente prédéfinie dans la base de données **msdb** nommée **WMIEventProviderNotificationQueue**. (Le service et la file d’attente sont créés dynamiquement par le fournisseur lorsqu’il se connecte pour la première fois à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .) Le fournisseur lit ensuite les données d’événement de cette file d’attente et les transforme en MOF (Managed Object Format) avant de les retourner à l’application. L'illustration ci-dessous montre ce processus.  
  
 ![Diagramme de flux du fournisseur WMI pour les événements de serveur](../../relational-databases/wmi-provider-server-events/media/wmi-provider-functional-spec.gif "Diagramme de flux du fournisseur WMI pour les événements de serveur")  
  
 Examinons, par exemple, la requête WQL suivante :  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS  
WHERE DatabaseName = 'AdventureWorks'  
```  
  
 En réponse à cette requête, le fournisseur WMI pour les événements serveur crée la notification d'événements équivalente dans la base de données cible :  
  
```  
USE AdventureWorks ;  
GO  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE  
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',   
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 Dans cet exemple, `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` est un identificateur [!INCLUDE[tsql](../../includes/tsql-md.md)] composé du préfixe `SQLWEP_` et d'un GUID. `SQLWEP` crée un GUID pour chaque identificateur. La valeur `A7E5521A-1CA6-4741-865D-826F804E5135` dans la `TO SERVICE` clause est le GUID qui identifie l’instance Broker dans la base de données **msdb** .  
  
 Pour plus d’informations sur l’utilisation de WQL, consultez [utilisation de WQL avec le fournisseur WMI pour les événements de serveur](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Les applications de gestion dirigent le fournisseur WMI pour les événements serveur vers une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en se connectant à un espace de noms WMI défini par le fournisseur. Le service WMI de Windows mappe cet espace de noms à la DLL de fournisseur, Sqlwep.dll, puis la charge en mémoire. Le fournisseur gère un espace de noms WMI pour les événements serveur pour chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le format est : \\ \\ . \\ *root*\Microsoft\SqlServer\ServerEvents racine \\ *instance_name*, où *instance_name* par défaut est MSSQLSERVER. Pour plus d’informations sur la façon de se connecter à un espace de noms WMI pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [utilisation de WQL avec le fournisseur WMI pour les événements de serveur](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 La DLL de fournisseur, Sqlwep.dll, est chargée une seule fois dans le service hôte WMI du système d'exploitation du serveur, indépendamment du nombre d'instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présentes sur le serveur.  
  
 Pour obtenir un exemple d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] application de gestion d’agent qui utilise le fournisseur WMI pour les événements de serveur, consultez [exemple : création d’une alerte de SQL Server agent à l’aide du fournisseur WMI pour les événements de serveur](https://technet.microsoft.com/library/ms186385.aspx). Pour obtenir un exemple d’application de gestion qui utilise le fournisseur WMI pour les événements de serveur dans le code managé, consultez [exemple : utilisation du fournisseur d’événements WMI dans du code managé](https://technet.microsoft.com/library/ms179315.aspx). Des informations supplémentaires sont également disponibles sur WMI dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Kit de développement logiciel (SDK).  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur WMI pour les concepts des événements de serveur](https://technet.microsoft.com/library/ms180560.aspx)  
  
  
