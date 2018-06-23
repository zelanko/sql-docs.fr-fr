---
title: Vs régulières. Connexions contextuelles | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c2966244c8b23f58bf0762ae758ab298cc26c76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053082"
---
# <a name="regular-vs-context-connections"></a>Vs régulières. Connexions contextuelles
  Si vous vous connectez à un serveur distant, utilisez toujours des connexions normales plutôt que des connexions contextuelles. Si vous devez vous connecter au même serveur sur lequel la procédure stockée ou la fonction est en cours d'exécution, utilisez la connexion contextuelle dans la majorité des cas. Ceci présente des avantages, notamment l'exécution dans le même espace de transaction et la non-obligation de s'authentifier à nouveau.  
  
 Qui plus est, le recours aux connexions contextuelles produit généralement de meilleures performances et garantit une utilisation plus réduite des ressources. La connexion contextuelle est une connexion in-process uniquement. Elle peut donc contacter « directement » le serveur en ignorant les couches transport et protocole réseau pour envoyer des instructions Transact-SQL et recevoir des résultats. Le processus d'authentification est également ignoré. La figure suivante présente les composants principaux du fournisseur managé `SqlClient` et explique également comment les divers composants interagissent l'un avec l'autre lors de l'utilisation d'une connexion normale et de la connexion contextuelle.  
  
 ![Chemins de code d’un contexte et connexion normale. ] (../../../database-engine/dev-guide/media/clrintdataaccess.gif "Chemins de code d’un contexte et connexion normale.")  
  
 La connexion contextuelle suit un chemin de code plus court et implique moins de composants. Vous pouvez donc vous attendre à des demandes et des résultats circulant vers et depuis le serveur plus rapidement qu'avec une connexion normale. Le temps d'exécution des requêtes sur le serveur est le même pour les connexions normales et contextuelles.  
  
 Dans certains cas, vous devrez peut-être ouvrir une connexion normale distincte sur le même serveur. Par exemple, il existe des restrictions d’utilisation de la connexion de contexte décrite dans [Restrictions sur les connexions normales et contextuelles](context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](context-connection.md)  
  
  