---
title: Connexions régulières vs Contexte Microsoft Docs
description: Dans SQL Server, vous devez parfois utiliser des connexions régulières pour les relevés Transact-SQL, mais les connexions contextuelles offrent des avantages en matière de performances et d’utilisation des ressources.
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
ms.openlocfilehash: 881b7463400665d22baaa9b19f13cb5949df0830
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485176"
---
# <a name="context-connections-vs-regular-connections"></a>Connexions contextuelles vs connexions régulières
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Si vous vous connectez à un serveur distant, utilisez toujours des connexions normales plutôt que des connexions contextuelles. Si vous devez vous connecter au même serveur sur lequel la procédure stockée ou la fonction est en cours d'exécution, utilisez la connexion contextuelle dans la majorité des cas. Ceci présente des avantages, notamment l'exécution dans le même espace de transaction et la non-obligation de s'authentifier à nouveau.  
  
 Qui plus est, le recours aux connexions contextuelles produit généralement de meilleures performances et garantit une utilisation plus réduite des ressources. La connexion contextuelle est une connexion en cours de traitement seulement, de sorte qu’elle peut contacter le serveur "directement" en contournant le protocole réseau et les couches de transport pour envoyer des relevés Transact-SQL et recevoir des résultats. Le processus d'authentification est également ignoré. Le chiffre suivant montre les principaux composants du fournisseur géré **De SqlClient,** ainsi que la façon dont les différents composants interagissent les uns avec les autres lors de l’utilisation d’une connexion régulière, et lors de l’utilisation de la connexion contextuelle.  
  
 ![Chemins de code d'un contexte et connexion normale.](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Chemins de code d'un contexte et connexion normale.")  
  
 La connexion contextuelle suit un chemin de code plus court et implique moins de composants. Vous pouvez donc vous attendre à des demandes et des résultats circulant vers et depuis le serveur plus rapidement qu'avec une connexion normale. Le temps d'exécution des requêtes sur le serveur est le même pour les connexions normales et contextuelles.  
  
 Dans certains cas, vous devrez peut-être ouvrir une connexion normale distincte sur le même serveur. Par exemple, il existe certaines restrictions à l’utilisation de la connexion contextuelle, décrite dans [Restrictions sur les connexions régulières et contextuelles](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
