---
title: catalog.master_properties (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbbb6599c4b50e30b566a9ec105b44d1b2853b9c
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912515"
---
# <a name="catalogmaster_properties-ssisdb-database"></a>catalog.master_properties (base de données SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Affiche les propriétés d’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master.

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar (256)**|Nom de la propriété de Scale Out Master.|  
|property_value|**nvarchar(max)**|Valeur de la propriété de Scale Out Master.|

## <a name="remarks"></a>Notes
Cette vue affiche une ligne pour chaque propriété de Scale Out Master. Les propriétés affichées par cette vue incluent les éléments suivants :

|Nom de la propriété|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|Serveur SQL Server qui héberge la base de données du journal.|
|**LAST_ONLINE_TIME**|Dernière fois que Scale Out Master était en ligne.|
|**MACHINE_IP**|Adresse IP de la machine.|
|**MACHINE_NAME**|Nom de l'ordinateur.|
|**MASTER_ADDRESS**|Point de terminaison de Scale Out Master.|
|**MASTER_SERVICE_PORT**|Port dans le point de terminaison de Scale Out Master.|
|**SSLCERT_THUMBPRINT**|Empreinte du certificat de Scale Out Master.|

## <a name="permissions"></a>Autorisations
Tous les membres du rôle de base de données public ont l’autorisation de lecture sur cette vue. 
