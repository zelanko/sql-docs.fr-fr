---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 96b4deb3bf0c7d660779781f9d76aac785ca12ca
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415128"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|260|  
|Source de l'événement|Runtime de base de données locale SQL Server 12.0|  
|Composant|API d'exécution de la base de données locale|  
|Texte du message|Le chemin complet du dossier d'instance de base de données locale est plus long que MAX_PATH. L’instance doit être stockée dans le dossier : %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\< nom de l’instance\>.|  
  
## <a name="explanation"></a>Explication  
 Le chemin d'accès où l'instance doit être stockée est plus long que MAX_PATH.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Créez un nouveau chemin d'accès plus court que MAX_PATH.  
  
  
