---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c59f74a3e0584ec70eea4832936d7dc08cc74087
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52397743"
---
# <a name="mssqlserver21898"></a>MSSQLSERVER_21898
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21898|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21898|  
|Texte du message|Le serveur de publication '%s' utilise la base de données de distribution '%s' et non '%s', requise pour héberger la base de données de publication '%s'. Exécutez `sp_changedistpublisher` sur le serveur de distribution '%s' pour modifier la base de données de distribution utilisée par le serveur de publication sur '%s'.|  
  
## <a name="explanation"></a>Explication  
 `sp_validate_redirected_publisher` interroge msdb.dbo.MSdistpublishers sur le serveur de distribution local pour vérifier que la base de données de distribution utilisée par le nouveau serveur de publication est identique à la base de données de distribution utilisée par le serveur de publication d’origine. Cette erreur est retournée lorsque ces bases de données diffèrent, faisant du serveur de publication un hôte incorrect pour la base de données du serveur de publication.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez la procédure stockée `sp_changedistpublisher` pour modifier la base de données de distribution du nouveau serveur de publication et utiliser celle utilisée par le serveur de publication d'origine.  
  
> [!NOTE]  
>  L'exécution de `sp_changedistpublisher` résout le problème si la base de données de distribution incorrecte a été configurée lorsque `sp_adddistpublisher` a été exécuté sur le serveur de distribution pour le serveur de publication. Toutefois, si le serveur de publication distant possède des publications existantes provenant d'une autre base de données de publication qui utilisent la base de données de distribution identifiée, cette modification n'est pas appropriée. La réplication utilisant la base de données de distribution nommée doit être systématiquement supprimée puis rétablie à l’aide de la base de données de distribution d’origine du serveur de publication pour que le nouveau serveur de publication fonctionne comme un hôte approprié.  
  
  
