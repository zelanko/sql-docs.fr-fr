---
title: Catalog.event_message_context | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b7aeb07c52f7ed00aa5a6a29cdd054258cb62d65
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogeventmessagecontext"></a>catalog.event_message_context
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche des informations sur les conditions associées aux messages d'événements d'exécution, pour les exécutions sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|Context_id|bigint|ID unique du contexte de l'erreur.|  
|Event_message_id|bigint|ID unique du message auquel le contexte est associé.|  
|Context_depth|int|À mesure que la profondeur augmente, le contexte s'éloigne de l'erreur. Lorsqu'une erreur se produit, la profondeur du contexte commence à 1. La valeur 0 indique l'état du package avant le démarrage de l'exécution.|  
|Package_path|Nvarchar(max)|Chemin d'accès au package de la source du contexte.|  
|Context_type|smallint|Type de l'objet qui est la source du contexte. Consultez le **notes** section pour obtenir la liste des types de contexte.|  
|Context_source_name|Nvarchar(4000)|Nom de l'objet qui est la source du contexte.|  
|Context_source_id|Nvarchar(38)|ID unique de l'objet qui est la source du contexte.|  
|Property_name|Nvarchar(4000)|Nom de la propriété associée à la source du contexte.|  
|Property_value|Sql_variant|Valeur de la propriété associée à la source du contexte.|  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant répertorie les types de contexte.  
  
||||  
|-|-|-|  
|Valeur du type de contexte|Nom de type| Description|  
|10|Tâche|État d'une tâche lorsqu'une erreur s'est produite.|  
|20|Pipeline|L'erreur provient d'un composant de pipeline : source, destination ou composant de transformation.|  
|30|Séquence|État d'une séquence.|  
|40|Boucle For|État d'une boucle For.|  
|50|Boucle Foreach|État d'une boucle Foreach.|  
|60|Package|État du package lorsqu'une erreur s'est produite.|  
|70|Variable|Valeur de variable|  
|80|Gestionnaire de connexions|Propriétés d'un gestionnaire de connexions.|  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'opération  
  
-   L’appartenance à la **ssis_admin** rôle de base de données.  
  
-   L’appartenance à la **sysadmin** rôle de serveur.  
  
  

