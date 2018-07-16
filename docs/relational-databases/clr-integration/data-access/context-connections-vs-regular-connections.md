---
title: Visual Studio standard. Connexions contextuelles | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 938ae2b6a740f793a87a1ed634d2d02b061a6123
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356321"
---
# <a name="context-connections-vs-regular-connections"></a>Connexions contextuelles et. Connexions normales
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Si vous vous connectez à un serveur distant, utilisez toujours des connexions normales plutôt que des connexions contextuelles. Si vous devez vous connecter au même serveur sur lequel la procédure stockée ou la fonction est en cours d'exécution, utilisez la connexion contextuelle dans la majorité des cas. Ceci présente des avantages, notamment l'exécution dans le même espace de transaction et la non-obligation de s'authentifier à nouveau.  
  
 Qui plus est, le recours aux connexions contextuelles produit généralement de meilleures performances et garantit une utilisation plus réduite des ressources. La connexion contextuelle est une connexion in-process uniquement. Elle peut donc contacter « directement » le serveur en ignorant les couches transport et protocole réseau pour envoyer des instructions Transact-SQL et recevoir des résultats. Le processus d'authentification est également ignoré. La figure suivante montre les principaux composants de la **SqlClient** gérés fournisseur, ainsi que comment les différents composants interagissent entre eux lorsque vous utilisez une connexion normale et lors de l’utilisation de la connexion de contexte.  
  
 ![Chemins de code d’un contexte et connexion normale. ] (../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Chemins de code d’un contexte et connexion normale.")  
  
 La connexion contextuelle suit un chemin de code plus court et implique moins de composants. Vous pouvez donc vous attendre à des demandes et des résultats circulant vers et depuis le serveur plus rapidement qu'avec une connexion normale. Le temps d'exécution des requêtes sur le serveur est le même pour les connexions normales et contextuelles.  
  
 Dans certains cas, vous devrez peut-être ouvrir une connexion normale distincte sur le même serveur. Par exemple, il existe certaines restrictions sur l’utilisation de la connexion de contexte décrite dans [Restrictions sur les connexions normales et contextuelles](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
