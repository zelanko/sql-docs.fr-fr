---
title: Utilisation de WQL avec le fournisseur WMI pour les événements de serveur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 18c4b6448438ebb8c95f999569d51edfecf04206
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211588"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a>Utilisation de WQL avec le fournisseur WMI pour les événements de serveur
  Les applications de gestion accèdent aux événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via le fournisseur WMI pour les événements serveur en émettant des instructions WQL (WMI Query Language). Le langage WQL est un sous-ensemble simplifié du langage SQL, avec quelques extensions spécifiques à WMI. Pour utiliser le WQL, une application extrait un type d'événement sur une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une base de données ou un objet de base de données (le seul objet pris en charge actuellement est la file d'attente). Le fournisseur WMI pour les événements serveur traduit la requête en une notification d’événement qui est créée dans la base de données cible pour les notifications d’événements étendues à la base de données ou à l’étendue de l’objet, ou dans la base de données **Master** pour les notifications d’événements d’étendue de serveur.  
  
 Examinons, par exemple, la requête WQL suivante :  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 À partir de cette requête, le fournisseur WMI tente de produire l'équivalent de cette notification d'événements sur le serveur cible :  
  
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
  
 L'argument de la clause `FROM` de la requête WQL (`DDL_DATABASE_LEVEL_EVENTS`) peut être n'importe quel événement valide sur lequel il est possible de créer une notification d'événements. Les arguments des clauses `SELECT` et `WHERE` peuvent spécifier n'importe quelle propriété d'événement associée à un événement ou à son événement parent. Pour obtenir la liste des événements et des propriétés d’événement valides, consultez [notifications d’événements (moteur de base de données)](https://technet.microsoft.com/library/ms182602.aspx).  
  
 La syntaxe WQL suivante est prise en charge explicitement par le fournisseur WMI pour les événements serveur. Une syntaxe WQL additionnelle peut être spécifiée, mais elle n'est pas spécifique à ce fournisseur et est analysée à la place par le service hôte WMI. Pour plus d'informations sur le langage de requêtes WMI (WQL), consultez la documentation WQL sur MSDN (Microsoft Developer Network).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition  
```  
  
## <a name="arguments"></a>Arguments  
 *event_property*  
 Est la propriété d'un événement. `PostTime`, `SPID` et `LoginName` en sont des exemples. Recherchez chaque événement listé dans [fournisseur WMI pour les classes et propriétés d’événements de serveur](wmi-provider-for-server-events-classes-and-properties.md) afin de déterminer les propriétés qu’il contient. Par exemple, l'événement DDL_DATABASE_LEVEL_EVENTS contient les propriétés `DatabaseName` et `UserName`. Il hérite également des propriétés `SQLInstance`, `LoginName`, `PostTime`, `SPID` et `ComputerName` de ses événements parents.  
  
 **,** *... n*  
 Indique que les *event_property* peuvent être interrogées plusieurs fois, séparées par des virgules.  
  
 \*  
 Spécifie que toutes les propriétés associées à un événement sont interrogées.  
  
 *event_type*  
 Est un événement sur lequel une notification d'événements peut être créée. Pour obtenir la liste des événements disponibles, consultez [fournisseur WMI pour les classes et propriétés d’événements de serveur](https://technet.microsoft.com/library/ms186449.aspx). Notez que les noms de *type d’événement* correspondent aux mêmes *event_type* | *event_group* qui peuvent être spécifiés quand vous créez manuellement une notification d’événement à l’aide de l’événement créer une notification d’événements. CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS et TRC_DATABASE sont des exemples de *type d’événement* .  
  
> [!NOTE]  
>  Certaines procédures stockées système qui exécutent des opérations de type DDL peuvent également déclencher des notifications d'événements. Testez vos notifications d'événements pour déterminer leur réponse aux procédures stockées du système qui sont exécutées. Par exemple, l’instruction CREATe TYPE et la procédure stockée **sp_addtype** déclenchent toutes deux une notification d’événement qui est créée sur un événement CREATE_TYPE. Toutefois, la procédure stockée **sp_rename** ne déclenche pas de notifications d’événements. Pour plus d’informations, consultez[événements DDL](../triggers/ddl-events.md).  
  
 *where_condition*  
 Est un prédicat de requête de la clause WHERE constitué de noms de *event_property* et d’opérateurs logiques et de comparaison. Le *where_condition* détermine l’étendue dans laquelle la notification d’événements correspondante est inscrite dans la base de données cible. Il peut également servir de filtre pour cibler un schéma ou un objet particulier à partir duquel interroger *event_type.* Pour plus d'informations, consultez la section « Notes » plus loin dans cette rubrique.  
  
 Seul l'opérande `=` peut être utilisé avec `DatabaseName`, `SchemaName` et `ObjectName`. D'autres expressions ne peuvent pas être utilisées avec ces propriétés d'événement.  
  
## <a name="remarks"></a>Notes  
 La *where_condition* de la syntaxe du fournisseur WMI pour les événements de serveur détermine les éléments suivants :  
  
-   Portée par laquelle le fournisseur tente de récupérer les *event_type*spécifiées : le niveau serveur, le niveau base de données ou le niveau objet (le seul objet pris en charge actuellement est la file d’attente). En dernier ressort, cette étendue détermine le type de notification d'événements créé dans la base de données cible. Ce processus est appelé inscription de notification d'événements.  
  
-   La base de données, le schéma et l'objet, le cas échéant, sur lequel s'effectue l'inscription.  
  
 Le fournisseur WMI pour les événements serveur utilise un algorithme ascendant pour produire l'étendue la plus étroite possible pour l'EVENT NOTIFICATION sous-jacent. L'algorithme essaie de réduire l'activité interne sur le serveur, ainsi que le trafic réseau entre l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le processus hôte de WMI. Le fournisseur examine les *event_type* spécifiées dans la clause from et les conditions de la clause WHERE, puis tente d’enregistrer la notification d’événement sous-jacente avec l’étendue la plus étroite possible. Si le fournisseur ne peut pas effectuer l'inscription avec l'étendue la plus étroite, il essaie de s'inscrire successivement à des étendues supérieures jusqu'à ce qu'une inscription réussisse enfin. S'il atteint l'étendue la plus élevée (niveau serveur) et échoue, il retourne une erreur au consommateur.  
  
 Par exemple, si DatabaseName =**'** AdventureWorks **'** est spécifié dans la clause WHERE, le fournisseur essaie d’inscrire une notification d’événement dans [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] la base de données. Si la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] existe et que le client appelant a les autorisations requises pour créer une notification d'événements dans [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], l'inscription est réussie. Sinon, une tentative a lieu pour enregistrer la notification d'événements au niveau serveur. L'inscription réussit si le client WMI a les autorisations requises. Toutefois, dans ce scénario, les événements ne sont pas retournés au client tant que la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] n'a pas été créée.  
  
 La *where_condition* peut également servir de filtre pour limiter en outre la requête à une base de données, un schéma ou un objet spécifique. Examinons, par exemple, la requête WQL suivante :  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 Selon le résultat de la procédure d'inscription, cette requête WQL peut être inscrite au niveau base de données ou au niveau serveur. Toutefois, même si elle est inscrite au niveau serveur, le fournisseur filtre en fin de compte tous les événements `ALTER_TABLE` qui ne s'appliquent pas à la table `AdventureWorks.Sales.SalesOrderDetail`. En d'autres termes, le fournisseur ne retourne que les propriétés des événements `ALTER_TABLE` qui se produisent sur cette table spécifique.  
  
 Si une expression composée telle que `DatabaseName='AW1'` OR `DatabaseName='AW2'` est spécifiée, une tentative a lieu pour inscrire une seule notification d'événements dans l'étendue du serveur au lieu de deux notifications d'événements distinctes. L'inscription réussit si le client appelant a les autorisations requises.  
  
 Si `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` tous les sont spécifiés `WHERE` dans la clause, une tentative d’enregistrement de la notification d’événement directement `Z` sur l' `X`objet dans le schéma est effectuée. L'inscription réussit si le client a les autorisations requises. Notez que, actuellement, les événements de niveau objet sont pris en charge uniquement sur les files d’attente et uniquement pour le *event_type*QUEUE_ACTIVATION.  
  
 Notez que certains événements ne peuvent pas être interrogés dans quelque étendue que ce soit. Par exemple, une requête WQL sur un événement de trace tel que Lock_Deadlock ou un groupe d'événements de trace tel que TRC_LOCKS ne peut être inscrite qu'au niveau serveur. De même, l'événement CREATE_ENDPOINT et le groupe d'événements DDL_ENDPOINT_EVENTS ne peuvent également être inscrits qu'au niveau serveur. Pour plus d’informations sur l’étendue appropriée pour l’inscription des événements, consultez [conception de notifications d’événements](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx). Une tentative d’inscription d’une requête WQL dont les *event_type* peuvent uniquement être inscrits au niveau du serveur est toujours effectuée au niveau du serveur. L'inscription réussit si le client WMI a les autorisations requises. Sinon, une erreur est retournée au client. Dans certains cas, cependant, vous pouvez encore utiliser la clause WHERE comme filtre pour les événements de niveau serveur en fonction des propriétés qui correspondent à l'événement. Par exemple, de nombreux événements de trace ont une propriété `DatabaseName` qui peut être utilisée dans la clause WHERE comme filtre.  
  
 Les notifications d’événements d’étendue de serveur sont créées dans la base de données **Master** et peuvent être interrogées pour les métadonnées à l’aide de l’affichage catalogue [sys. server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) .  
  
 Les notifications d’événements au niveau de la base de données ou de l’étendue objet sont créées dans la base de données spécifiée et peuvent être interrogées pour les métadonnées à l’aide de l’affichage catalogue [sys. event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql) . (Vous devez préfixer l'affichage catalogue avec le nom correspondant de la base de données.)  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-querying-for-events-at-the-server-scope"></a>R. Interrogation des événements dans l'étendue du serveur  
 La requête WQL suivante extrait toutes les propriétés d'événement pour tout événement de trace `SERVER_MEMORY_CHANGE` qui se produit sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a>B. Interrogation des événements dans l'étendue de la base de données  
 La requête WQL suivante extrait les propriétés d'événement spécifiques pour tout événement qui se produit dans la base de données `AdventureWorks` et qui existe sous le groupe d'événements `DDL_DATABASE_LEVEL_EVENTS`.  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a>C. Interrogation des événements dans l'étendue de la base de données, avec un filtre par schéma et par objet  
 La requête suivante extrait toutes les propriétés d'événement pour tout événement `ALTER_TABLE` qui se produit sur la table `AdventureWorks.Sales.SalesOrderDetail`.  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur WMI pour les concepts des événements de serveur](https://technet.microsoft.com/library/ms180560.aspx)   
 [Notifications d'événements (moteur de base de données)](https://technet.microsoft.com/library/ms182602.aspx)  
  
  
