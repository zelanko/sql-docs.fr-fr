---
title: Présentation du fournisseur WMI pour les événements serveur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2deedb64e5c8995524978a19b02110a068bde08d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68195812"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a>Présentation du fournisseur WMI pour les événements serveur
  Le fournisseur WMI pour les événements de serveur vous permet d'utiliser WMI (Windows Management Instrumentation) pour surveiller les événements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ce fournisseur fonctionne en transformant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un objet WMI managé. Tout événement qui peut générer une notification d'événements dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut tirer parti de WMI via ce fournisseur. En outre, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en tant qu'application de gestion qui interagit avec WMI, peut répondre à ces événements, ce qui augmente l'étendue des événements traités par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par rapport aux versions antérieures.  
  
 Les applications de gestion telles que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent accéder aux événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via le fournisseur WMI pour les événements serveur en publiant des instructions WQL (WMI Query Language). Le langage WQL est un sous-ensemble simplifié du langage SQL, avec quelques extensions spécifiques à WMI. À l'aide du langage WQL, une application récupère un type d'événement à partir d'une base de données ou d'un objet de base de données spécifique. Le fournisseur WMI pour les événements serveur traduit la requête en une notification d'événements, ce qui entraîne la création effective d'une notification d'événements dans la base de données cible. Pour plus d’informations sur le fonctionnement des notifications d’événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [fournisseur WMI pour les Concepts des événements serveur](https://technet.microsoft.com/library/ms180560.aspx). Les événements qui peuvent être interrogés sont répertoriés dans [fournisseur WMI pour les Classes d’événements de serveur et les propriétés](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).  
  
 Lorsqu’un événement survient qui déclenche la notification d’événement pour envoyer un message, le message est envoyé à un service cible prédéfini dans **msdb** qui est nommé **SQL/Notifications/ProcessWMIEventProviderNotification/v1.0**. Le service place l’événement dans une file d’attente prédéfinie dans **msdb** qui est nommé **WMIEventProviderNotificationQueue**. (Le service et la file d’attente sont créés dynamiquement par le fournisseur lorsqu’il se connecte d’abord à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) Le fournisseur lit les données d’événement à partir de cette file d’attente, puis convertit au format d’objet géré (MOF) avant de retourner à l’application. L'illustration ci-dessous montre ce processus.  
  
 ![Diagramme de flux du fournisseur WMI pour les événements serveur](../../../2014/database-engine/dev-guide/media/wmi-provider-functional-spec.gif "diagramme de flux du fournisseur WMI pour les événements serveur")  
  
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
  
 Dans cet exemple, `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` est un identificateur [!INCLUDE[tsql](../../includes/tsql-md.md)] composé du préfixe `SQLWEP_` et d'un GUID. `SQLWEP` crée un GUID pour chaque identificateur. La valeur `A7E5521A-1CA6-4741-865D-826F804E5135` dans le `TO SERVICE` clause est le GUID qui identifie l’instance de service broker dans la **msdb** base de données.  
  
 Pour plus d’informations sur l’utilisation du langage WQL, consultez [à l’aide de WQL avec le fournisseur WMI pour les événements serveur](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Les applications de gestion dirigent le fournisseur WMI pour les événements serveur vers une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en se connectant à un espace de noms WMI défini par le fournisseur. Le service WMI de Windows mappe cet espace de noms à la DLL de fournisseur, Sqlwep.dll, puis la charge en mémoire. Le fournisseur gère un espace de noms WMI pour les événements serveur pour chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et le format est : \\ \\.\\ *racine*\Microsoft\SqlServer\ServerEvents\\*nom_instance*, où *nom_instance* valeur par défaut est MSSQLSERVER. Pour plus d’informations sur comment se connecter à un espace de noms WMI pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [à l’aide de WQL avec le fournisseur WMI pour les événements serveur](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 La DLL de fournisseur, Sqlwep.dll, est chargée une seule fois dans le service hôte WMI du système d'exploitation du serveur, indépendamment du nombre d'instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présentes sur le serveur.  
  
 Pour obtenir un exemple d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] application de gestion de l’Agent qui utilise le fournisseur WMI pour les événements de serveur, consultez [exemple : Création d’une alerte de l’Agent SQL Server à l’aide du fournisseur WMI pour les événements serveur](https://technet.microsoft.com/library/ms186385.aspx). Pour obtenir un exemple d’application de gestion qui utilise le fournisseur WMI pour les événements serveur dans le code managé, consultez [exemple : Utilisation du fournisseur d’événements WMI dans Code managé](https://technet.microsoft.com/library/ms179315.aspx). Vous trouverez plus d’informations sur WMI dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur WMI pour les concepts des événements de serveur](https://technet.microsoft.com/library/ms180560.aspx)  
  
  
