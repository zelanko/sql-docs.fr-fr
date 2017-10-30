---
title: "Catalog.master_properties (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: 0fcbdca57c7764eaec758d2ad9ef3ab8675a3a9b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/08/2017

---
# <a name="catalogmasterproperties-ssisdb-database"></a>Catalog.master_properties (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Affiche les propriétés de la [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] échelle Out principale.

|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar (256)**|Le nom de la montée en charge la propriété principale.|  
|property_value|**nvarchar(max)**|La valeur de la montée en charge la propriété principale.|

## <a name="remarks"></a>Notes
Cette vue affiche une ligne pour chaque propriété maître de montée. Les propriétés affichées par cette vue incluent les éléments suivants :

|Nom de la propriété| Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|Le serveur SQL Server de base de données du journal se trouve dans.|
|**LAST_ONLINE_TIME**|La dernière fois lorsque la mise à l’échelle des maître est en ligne.|
|**MACHINE_IP**|L’adresse IP de l’ordinateur.|
|**NOM_ORDINATEUR**|Nom de l'ordinateur.|
|**MASTER_ADDRESS**|Le point de terminaison de mise à l’échelle des Master.|
|**MASTER_SERVICE_PORT**|Le port du point de terminaison de mise à l’échelle des Master.|
|**SSLCERT_THUMBPRINT**|L’empreinte numérique du certificat de mise à l’échelle des Master.|

## <a name="permissions"></a>Permissions
Tous les membres du rôle de base de données public ont accès en lecture pour cette vue. 

