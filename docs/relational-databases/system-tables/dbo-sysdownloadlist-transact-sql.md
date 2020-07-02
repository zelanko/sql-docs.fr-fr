---
title: dbo.sysdownloadlist (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1c3918f18076767e8fb198d21ee01d92c0e7cdd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85675053"
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Contient la file d'attente des instructions de téléchargement pour l'ensemble des serveurs cibles.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Colonne d'identité indiquant la séquence naturelle d'insertion des lignes|  
|**source_server**|**sysname**|Nom du serveur source|  
|**operation_code**|**tinyint**|Code d'opération pour le travail :<br /><br /> **1** = ins (insérer)<br /><br /> **2** = UPD (mise à jour)<br /><br /> **3** = del (supprimer)<br /><br /> **4** = démarrer<br /><br /> **5** = arrêter|  
|**object_type**|**tinyint**|Code du type d'objet.|  
|**object_id** <sup>1</sup>|**uniqueidentifier**|Numéro d'identification de l'objet.|  
|**target_server**|**sysname**|Nom du serveur cible|  
|**error_message**|**nvarchar(1024)**|Message d'erreur si le serveur cible rencontre une erreur lors du traitement de la ligne spécifique|  
|**date_posted**|**datetime**|Date et heure à laquelle le travail a été posté vers le serveur cible|  
|**date_downloaded**|**datetime**|Date et heure à laquelle le travail a été téléchargé pour la dernière fois|  
|**statut**|**tinyint**|État du travail :<br /><br /> **0** = pas encore téléchargé<br /><br /> **1** = téléchargé avec succès|  
|**deleted_object_name**|**sysname**|Nom de l'objet supprimé.|  
  
 <sup>1</sup> la colonne **object_id** peut avoir la valeur **-1**, qui correspond à la valeur All si l' **operation_code** colonne est la valeur Delete.  
  
  
