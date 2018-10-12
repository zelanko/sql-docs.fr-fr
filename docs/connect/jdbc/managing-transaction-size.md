---
title: Gestion de la taille de Transaction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 82900342-bc80-445f-98a4-468a303aae1e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22ef6f66c6a0f1685b824c9c89689465c53f4d2d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810597"
---
# <a name="managing-transaction-size"></a>Gestion de la taille des transactions
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lorsque vous travaillez avec des transactions, il est important qu'elles soient aussi petites que possible. Le mode par défaut de validation automatique, que la méthode [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md) permet d’activer ou de désactiver, valide chaque action automatiquement. Pour la plupart des développeurs, il s'agit du mode le plus facile à utiliser.  
  
 Lorsque vous utilisez des transactions manuelles, assurez-vous que votre code valide les transactions le plus rapidement possible. Le fait de laisser une transaction ouverte empêche d'autres utilisateurs d'accéder aux données. Par exemple, en programmation, il est judicieux de mettre un appel de restauration dans votre bloc catch et un appel de validation dans le bloc finally. Toutefois, cela dépend de la conception de votre application.  
  
 Le fait de garder une taille de transactions la plus petite possible améliore l'accès simultané. Par exemple, si vous démarrez une transaction manuelle et que vous modifiez 10 000 lignes dans une table de 20 000 lignes, tous les autres utilisateurs se verront dans l'incapacité d'accéder à la moitié de la table, ne serait-ce que pour lire les données. La réduction de vos modifications à 2 000 lignes laisse 90 pour cent de la table disponible.  
  
 En outre, assurez-vous d'utiliser le paramètre de délai d'attente de verrou si votre application s'attend à rencontrer des problèmes de blocage et doit les éviter grâce à l'expiration du délai d'attente. Pour cela, utilisez la méthode [setLockTimeout](../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md). La valeur par défaut pour le délai d'attente de verrou est -1, ce qui signifie que le blocage durera tant que l'application attendra le verrou. Vous pouvez définir le délai d'attente de verrou à 30 secondes, ce qui provoquera l'expiration du délai d'attente de connexion bloquée après 30 secondes si elle est bloquée par une autre connexion.  
  
## <a name="see-also"></a> Voir aussi  
 [Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
