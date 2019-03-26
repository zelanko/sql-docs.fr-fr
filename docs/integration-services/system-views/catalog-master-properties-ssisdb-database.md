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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 04f04b8847dbdfac12f5b78c3eabb3b493e2d895
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275225"
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Affiche les propriétés d’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master.

|Nom de colonne|Type de données|Description|  
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
