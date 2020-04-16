---
title: sys.bandwidth_usage (Base de données Azure SQL) Microsoft Docs
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
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "67942575"
---
# <a name="sysbandwidth_usage-azure-sql-database"></a>sys.bandwidth_usage (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

> [!NOTE]
> Cela ne [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]s’applique qu’au V11.  
  
 Retourne les informations sur la bande passante réseau utilisée par chaque base de données dans un ** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] serveur de base de données V11**, . Chaque ligne retournée pour une base de données donnée résume une direction unique et une classe d'utilisation sur une période d'une heure.  
  
 **Cela a été déprécié dans un [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].**  
  
 La **vue sys.bandwidth_usage** contient les colonnes suivantes.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**time**|Heure à laquelle la bande passante a été consommée. Les lignes de cette vue sont par heure. Par exemple, 2009-09-19 02:00:00.000 indique que la bande passante a été consommée le 19 septembre 2009 entre 2h00 et 3h00.|  
|**database_name**|Nom de la base de données qui a utilisé la bande passante.|  
|**direction**|Type de bande passante utilisé, un des suivants :<br /><br /> Ingress: Données qui se [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]déplace dans le .<br /><br /> Egress: Données qui se [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]déplace hors de la .|  
|**class**|Classe de bande passante utilisée, une des suivantes :<br />Interne : Données qui se déplacent au sein de la plate-forme Azure.<br />Externe : Données qui sortent de la plate-forme Azure.<br /><br /> Cette classe est retournée uniquement si la base de données est engagée dans une relation de copie continue entre des régions ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]). Si une base de données donnée ne participe à aucune relation de copie continue, les lignes « Interlink » ne sont pas retournées. Pour plus d'informations, consultez la section « Notes », plus loin dans cette rubrique.|  
|**time_period**|La période durant laquelle l'utilisation est survenue est Peak (heures de pointe) ou OffPeak (heures creuses). La période de pointe (Peak) repose sur la zone dans laquelle le serveur a été créée. Par exemple, si un serveur a été créé dans la zone « US_Northwest », la période de pointe est définie comme étant entre 10h00 et et 18h00 PST.|  
|**Quantité**|Quantité de bande passante, en kilo-octets (Ko), qui a été utilisée.|  
  
## <a name="permissions"></a>Autorisations

 Cette vue n’est disponible que dans la base de données **principale** de la base de données du serveur.  
  
## <a name="remarks"></a>Notes  
  
### <a name="external-and-internal-classes"></a>Classes externes et internes

 Pour chaque base de données utilisée à un moment donné, le **sys.bandwidth_usage** vue renvoie des lignes qui montrent la classe et la direction de l’utilisation de la bande passante. L'exemple suivant illustre les données qui peuvent être exposées pour une base de données donnée. Dans cet exemple, la date et l'heure sont 2012-04-21 17h00 : 00, au cours d'une période de pointe. Le nom de la base de données est Db1. Dans cet exemple, **sys.bandwidth_usage** a retourné une rangée pour les quatre combinaisons des directions Ingress et Egress et des classes externes et internes, comme suit:  
  
|time|database_name|direction|class|time_period|quantité|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|Entrée|Externe|Peak|66|  
|2012-04-21 17:00:00|Db1|Sortie|Externe|Peak|741|  
|2012-04-21 17:00:00|Db1|Entrée|Interne|Peak|1052|  
|2012-04-21 17:00:00|Db1|Sortie|Interne|Peak|3525|  
  
### <a name="interpreting-data-direction-for-ssgeodr"></a>Interprétation de la direction des données pour [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]

 Pour [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)], les données d'utilisation de la bande passante sont visibles dans la base de données master logique des deux côtés d'une relation de copie continue. Vous devez donc interpréter les indicateurs d’ingresse et d’évacuation du point de vue des bases de données que vous interrogez. Par exemple, envisagez un flux de réplication qui transfère 1 Mo de données du serveur source vers le serveur cible. Dans ce cas, sur le serveur source, ces données font partie des données totales envoyées, et sur le serveur cible elles sont enregistrées en tant que données reçues.  
  
> [!NOTE]  
> Le bloc de données transférées est du serveur source vers le serveur cible, dans la direction du flux de données utilisateur. Cependant, des données doivent être transférées dans l'autre direction.  
