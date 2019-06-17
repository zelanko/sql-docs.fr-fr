---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94439a6981a2cf891a55bcbda7498db83e1fa52e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62990566"
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
  
  
