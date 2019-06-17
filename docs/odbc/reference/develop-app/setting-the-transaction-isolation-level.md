---
title: Définition du niveau d’Isolation des transactions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: 64a037f0-5065-4f45-9669-6710404a540c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37b575f9e208b5a1b7fa03b170b74633da149c67
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63237875"
---
# <a name="setting-the-transaction-isolation-level"></a>Définition du niveau d’isolation des transactions
Pour définir le niveau d’isolation de transaction, une application utilise l’attribut de connexion de SQL_ATTR_TXN_ISOLATION. Si la source de données ne prend pas en charge le niveau d’isolation demandé, le pilote ou une source de données peut définir un niveau plus élevé. Pour déterminer quelles isolation des transactions niveaux d’une source de données prend en charge et le niveau d’isolation par défaut est, une application appelle **SQLGetInfo** avec les options SQL_TXN_ISOLATION_OPTION et SQL_DEFAULT_TXN_ISOLATION, respectivement.  
  
 Les niveaux supérieurs d’isolation des transactions offrent une protection optimale pour l’intégrité de la base de données. Transactions sérialisables sont garanties être affectée par d’autres transactions et par conséquent garanties pour maintenir l’intégrité de base de données.  
  
 Toutefois, un niveau plus élevé d’isolation des transactions peut diminuer les performances, car elle augmente les chances que l’application devra attendre les verrous sur les données à libérer. Une application peut spécifier un niveau inférieur d’isolation pour augmenter les performances dans les cas suivants :  
  
-   Quand il peut être garantie qu’aucune autre transaction n’existe qui peut-être interférer avec les transactions d’une application. Cette situation se produit uniquement dans certaines circonstances, par exemple quand une personne dans une petite entreprise conserve les fichiers de dBASE qui contiennent des données sur un ordinateur personnel et ne partage pas ces fichiers.  
  
-   Quand la vitesse est plus importante que la précision et de toutes les erreurs sont susceptibles d’être petit. Par exemple, supposons qu’une entreprise met à votre petit nombre de ventes et que les ventes importantes sont rares. Une transaction qui estime la valeur totale de toutes les ventes peut utiliser en toute sécurité le niveau d’isolation Read Uncommitted. Bien que la transaction inclut les commandes qui sont en cours ouvert ou fermé et sont par la suite de restauration, il seraient généralement annulent et la transaction serait beaucoup plus rapide, car chaque fois qu’il rencontre un tel ordre n’est pas bloqué.  
  
 Pour plus d’informations, consultez [d’accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).
