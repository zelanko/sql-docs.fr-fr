---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 957cb58c292f895e31ae01d9918af4872a29bd9d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415408"
---
# <a name="mssqlserver21899"></a>MSSQLSERVER_21899
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21899|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21899|  
|Texte du message|Échec de la requête effectuée sur le serveur de publication redirigé '%s' afin de déterminer s’il existe des entrées sysserver pour les abonnés du serveur de publication d’origine '%s'. Erreur '%d', message d’erreur '%s'.|  
  
## <a name="explanation"></a>Explication  
 `sp_validate_redirected_publisher` interroge les tables de métadonnées d'abonnement de la base de données du serveur de publication sur le serveur distant pour déterminer ses abonnés associés. L'erreur 21899 est retournée si cette requête échoue. La requête de validation requiert l'accès à la base de données publiée sur le serveur de publication redirigé. Si la connexion spécifiée lorsque `sp_adddistpublisher` est appelé pour le serveur de publication d'origine n'est pas autorisée pour accéder à la base de données publiée sur le serveur de publication redirigé, l'erreur 21899 est retournée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez le message d'erreur cité pour déterminer la cause de l'échec et prendre l'action corrective appropriée  
  
  
