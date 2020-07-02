---
title: Connexions régulières et contextuelles | Microsoft Docs
description: Dans SQL Server, vous devez parfois utiliser des connexions régulières pour les instructions Transact-SQL, mais les connexions de contexte offrent des avantages en termes de performances et d’utilisation des ressources.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: 6417a0121a7e290d711690fb0150fdbe908827dd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637515"
---
# <a name="context-connections-vs-regular-connections"></a>Connexions de contexte et connexions normales
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Si vous vous connectez à un serveur distant, utilisez toujours des connexions normales plutôt que des connexions contextuelles. Si vous devez vous connecter au même serveur sur lequel la procédure stockée ou la fonction est en cours d'exécution, utilisez la connexion contextuelle dans la majorité des cas. Ceci présente des avantages, notamment l'exécution dans le même espace de transaction et la non-obligation de s'authentifier à nouveau.  
  
 Qui plus est, le recours aux connexions contextuelles produit généralement de meilleures performances et garantit une utilisation plus réduite des ressources. La connexion de contexte est une connexion en mode in-process uniquement. elle peut donc contacter le serveur « directement » en contournant le protocole réseau et les couches de transport pour envoyer des instructions Transact-SQL et recevoir des résultats. Le processus d'authentification est également ignoré. L’illustration suivante montre les principaux composants du fournisseur géré **SqlClient** , ainsi que la manière dont les différents composants interagissent entre eux lors de l’utilisation d’une connexion normale, et lors de l’utilisation de la connexion contextuelle.  
  
 ![Chemins de code d'un contexte et connexion normale.](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Chemins de code d'un contexte et connexion normale.")  
  
 La connexion contextuelle suit un chemin de code plus court et implique moins de composants. Vous pouvez donc vous attendre à des demandes et des résultats circulant vers et depuis le serveur plus rapidement qu'avec une connexion normale. Le temps d'exécution des requêtes sur le serveur est le même pour les connexions normales et contextuelles.  
  
 Dans certains cas, vous devrez peut-être ouvrir une connexion normale distincte sur le même serveur. Par exemple, certaines restrictions s’appliquent à l’utilisation de la connexion contextuelle, décrite dans [restrictions sur les connexions régulières et de contexte](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
