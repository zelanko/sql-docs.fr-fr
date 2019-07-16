---
title: Sys.bandwidth_usage (base de données Azure SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- bandwidth_usage
- sys.bandwidth_usage
- bandwidth_usage_TSQL
- sys.bandwidth_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.bandwidth_usage
- bandwidth_usage
ms.assetid: 43ed8435-f059-4907-b5c0-193a258b394a
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ea963c07a15cd5c2db3cca113680026d3100936b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942575"
---
# <a name="sysbandwidthusage-azure-sql-database"></a>sys.bandwidth_usage (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

> [!NOTE]
> Cela s’applique uniquement au [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.* *  
  
 Retourne des informations sur la bande passante réseau utilisée par chaque base de données dans un  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] serveur de base de données V11**,. Chaque ligne retournée pour une base de données donnée résume une direction unique et une classe d'utilisation sur une période d'une heure.  
  
 **Cela a été déconseillée dans une [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].**  
  
 Le **sys.bandwidth_usage** vue contient les colonnes suivantes.  
  
|Column Name|Description|  
|-----------------|-----------------|  
|**time**|Heure à laquelle la bande passante a été consommée. Les lignes de cette vue sont par heure. Par exemple, 2009-09-19 02:00:00.000 indique que la bande passante a été consommée le 19 septembre 2009 entre 2h00 et 3h00.|  
|**database_name**|Nom de la base de données qui a utilisé la bande passante.|  
|**direction**|Type de bande passante utilisé, un des suivants :<br /><br /> Entrée : Les données sont déplacées dans le [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Sortie : Les données sont déplacées hors de la [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**class**|Classe de bande passante utilisée, une des suivantes :<br />Interne : Données qui sont déplacent au sein de la plateforme Azure.<br />Externes : Données qui se déplacent hors de la plateforme Azure.<br /><br /> Cette classe est retournée uniquement si la base de données est engagée dans une relation de copie continue entre des régions ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]). Si une base de données n’est pas inclus dans une relation de copie continue, les lignes « Interlink » ne sont pas retournés. Pour plus d’informations, consultez la section « Remarques » plus loin dans cette rubrique.|  
|**time_period**|La période de temps lorsque l’utilisation s’est produite est pointe ou fixes. La période de pointe (Peak) repose sur la zone dans laquelle le serveur a été créée. Par exemple, si un serveur a été créé dans la zone « US_Northwest », la période de pointe est définie comme étant entre 10h00 et et 18 h 00. PST.|  
|**Quantité**|Quantité de bande passante, en kilo-octets (Ko), qui a été utilisée.|  
  
## <a name="permissions"></a>Autorisations

 Cette vue est disponible uniquement dans le **master** base de données pour la connexion du principal au niveau du serveur.  
  
## <a name="remarks"></a>Notes  
  
### <a name="external-and-internal-classes"></a>Classes externes et internes

 Pour chaque base de données utilisée à un moment donné, le **sys.bandwidth_usage** vue retourne les lignes qui affichent la classe et la direction de l’utilisation de la bande passante. L'exemple suivant illustre les données qui peuvent être exposées pour une base de données donnée. Dans cet exemple, la date et l'heure sont 2012-04-21 17h00 : 00, au cours d'une période de pointe. Le nom de la base de données est Db1. Dans cet exemple, **sys.bandwidth_usage** a retourné une ligne pour chacune des quatre combinaisons de directions d’entrée et de sortie et des classes externes et internes, comme suit :  
  
|time|database_name|direction|class|time_period|quantity|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|Ingress|External|Peak|66|  
|2012-04-21 17:00:00|Db1|Sortie|Ressource externe|Peak|741|  
|2012-04-21 17:00:00|Db1|Entrée|Internal|Peak|1052|  
|2012-04-21 17:00:00|Db1|Egress|Interne|Peak|3525|  
  
### <a name="interpreting-data-direction-for-includessgeodrincludesssgeodr-mdmd"></a>Interprétation de la direction des données pour [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]

 Pour [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)], les données d'utilisation de la bande passante sont visibles dans la base de données master logique des deux côtés d'une relation de copie continue. Par conséquent, vous devez interpréter l’entrée et sortie des indicateurs de direction du point de vue des bases de données que vous interrogez. Par exemple, envisagez un flux de réplication qui transfère 1 Mo de données du serveur source vers le serveur cible. Dans ce cas, sur le serveur source, ces données font partie des données totales envoyées, et sur le serveur cible elles sont enregistrées en tant que données reçues.  
  
> [!NOTE]  
> Le bloc de données transférées est du serveur source vers le serveur cible, dans la direction du flux de données utilisateur. Cependant, des données doivent être transférées dans l'autre direction.  
