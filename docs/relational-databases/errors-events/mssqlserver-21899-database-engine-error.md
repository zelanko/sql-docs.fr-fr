---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c8e25f71f23742de35dcc8c9629181dd20af2f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667267"
---
# <a name="mssqlserver21899"></a>MSSQLSERVER_21899
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
**sp_validate_redirected_publisher** interroge les tables de métadonnées d’abonnement de la base de données du serveur de publication sur le serveur distant pour déterminer ses abonnés associés. L'erreur 21899 est retournée si cette requête échoue. La requête de validation requiert l'accès à la base de données publiée sur le serveur de publication redirigé. Si la connexion spécifiée quand **sp_adddistpublisher** est appelé pour le serveur de publication d’origine n’est pas autorisée pour accéder à la base de données publiée sur le serveur de publication redirigé, l’erreur 21899 est retournée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Consultez le message d'erreur cité pour déterminer la cause de l'échec et prendre l'action corrective appropriée  
  
