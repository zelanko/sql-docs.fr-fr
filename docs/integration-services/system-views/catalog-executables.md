---
title: catalog.executables | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a1811d0e5fc203b9a97336933c3943a684fb5c9a
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65714860"
---
# <a name="catalogexecutables"></a>catalog.executables 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette vue affiche une ligne pour chaque fichier exécutable dans l'exécution spécifiée.  
  
 Un exécutable est une tâche ou un conteneur que vous ajoutez au flux de contrôle d'un package.  
  
|Nom de colonne|**Data type**|Description|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Identificateur unique du fichier exécutable.|  
|execution_id|**bigint**|Identificateur unique de l'instance d'exécution.|  
|executable_name|**nvarchar(4000)**|Nom du fichier exécutable.|  
|executable_guid|**nvarchar(38)**|GUID du fichier exécutable.|  
|package_name|**nvarchar(260)**|Nom du package.|  
|package_path|**nvarchar(max)**|Chemin du package.|  
  
## <a name="permissions"></a>Autorisations  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
## <a name="remarks"></a>Notes   
  
