---
title: MSSQLSERVER_5515 | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: b67a2eba3337da6f5ef81bb0a071371628f96cee
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver5515"></a>MSSQLSERVER_5515
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|MSSQLSERVER|  
|ID d'événement|5515|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|FS_OPEN_CONTAINER_FAILED|  
|Texte du message|Impossible d'ouvrir le répertoire conteneur « %.*ls » du fichier FILESTREAM. Le système d'exploitation a retourné le code d'état Windows 0x%x.|  
  
## <a name="explanation"></a>Explication  
Le répertoire conteneur spécifié pour le fichier FILESTREAM ne peut pas être ouvert.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour la cause de l'erreur, consultez le code d'état Windows spécifique.  
  
