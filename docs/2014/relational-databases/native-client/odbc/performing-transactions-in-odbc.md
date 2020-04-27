---
title: Transactions dans ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ade18b71fa83c7acbb16cb7facd19dd3de61a2e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63143318"
---
# <a name="transactions-in-odbc"></a>Transactions dans ODBC
  Les transactions dans ODBC sont gérées connexion par connexion. Lorsqu'une application termine une transaction, elle valide ou restaure tout le travail effectué par le biais de tous les handles d'instruction sur cette connexion. Pour valider ou restaurer une transaction, les applications doivent appeler [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) au lieu de soumettre une instruction COMMIT ou ROLLBACK.  
  
 Une application appelle [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) pour basculer entre les deux modes ODBC de gestion des transactions :  
  
-   Mode de validation automatique  
  
     Chaque instruction est validée automatiquement lorsqu'elle est effectuée avec succès. Lorsque vous utilisez le mode de validation automatique, aucune autre fonction de gestion des transactions n'est requise.  
  
-   Mode de validation manuelle  
  
     Toutes les instructions exécutées sont incluses dans la même transaction jusqu'à ce qu'elle soit arrêtée spécifiquement en appelant **SQLEndTran**.  
  
 Le mode de validation automatique est le mode de gestion par défaut des transactions pour ODBC. Lorsqu'une connexion est établie, elle est en mode de validation automatique jusqu'à ce que **SQLSetConnectAttr** soit appelé pour basculer en mode de validation manuelle en désactivant le mode de validation automatique. Lorsqu'une application désactive la validation automatique, l'instruction suivante envoyée à la base de données démarre une transaction. La transaction reste ensuite active jusqu'à ce que l'application appelle **SQLEndTran** avec les options SQL_COMMIT ou SQL_ROLLBACK. La commande envoyée à la base de données après **SQLEndTran** démarre la transaction suivante.  
  
 Si une application bascule du mode de validation manuelle au mode de validation automatique, le pilote valide toutes les transactions actuellement ouvertes sur la connexion.  
  
 Les applications ODBC ne doivent pas utiliser d'instructions de transaction Transact-SQL telles que BEGIN TRANSACTION, COMMIT TRANSACTION ou ROLLBACK TRANSACTION, car cela peut provoquer un comportement indéterminé dans le pilote. Une application ODBC doit s'exécuter en mode de validation automatique et ne doit pas utiliser les instructions ni les fonctions de gestion des transactions, ou elle doit s'exécuter en mode de validation manuelle et utiliser la fonction ODBC **SQLEndTran** pour valider ou restaurer des transactions.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de transactions &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
