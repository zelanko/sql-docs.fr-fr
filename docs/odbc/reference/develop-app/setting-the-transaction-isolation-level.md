---
title: "Définition du niveau d’Isolation des transactions | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- isolation levels [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: 64a037f0-5065-4f45-9669-6710404a540c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 74c345bb8bdfae60a06576b43b655ef78e4a6dfc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-transaction-isolation-level"></a>Définition du niveau d’Isolation des transactions
Pour définir le niveau d’isolation de transaction, une application utilise l’attribut de connexion SQL_ATTR_TXN_ISOLATION. Si la source de données ne prend pas en charge le niveau d’isolation demandé, le pilote ou une source de données peut définir un niveau supérieur. Pour déterminer quelles transactions niveau d’isolation d’une source de données prend en charge et le niveau d’isolement par défaut est, une application appelle **SQLGetInfo** avec les options SQL_TXN_ISOLATION_OPTION et SQL_DEFAULT_TXN_ISOLATION, respectivement.  
  
 Les niveaux supérieurs d’isolation des transactions offrent une protection optimale pour l’intégrité des données de la base de données. Les transactions sont garanties pour être non affecté par d’autres transactions et par conséquent garanties pour conserver l’intégrité de base de données.  
  
 Toutefois, un niveau supérieur d’isolation des transactions peut diminuer les performances, car elle augmente les chances que l’application devra attendre les verrous sur les données à libérer. Une application peut spécifier un niveau inférieur de l’isolation pour augmenter les performances dans les cas suivants :  
  
-   Lorsqu’il est garanti qu’aucune autre transaction n’existant peut interférer avec les transactions d’une application. Cette situation se produit uniquement dans certaines circonstances, par exemple si une personne d’une petite entreprise met à jour les fichiers dBASE qui contiennent des données sur un ordinateur personnel et ne partage pas ces fichiers.  
  
-   Quand la vitesse est plus importante que la précision et les erreurs sont susceptibles d’être petit. Par exemple, supposons qu’une société fait petit nombre de ventes et que les ventes de grande taille sont rares. Une transaction qui détermine la valeur totale de toutes les ventes peut utiliser en toute sécurité le niveau d’isolation Read Uncommitted. Bien que la transaction inclut les commandes qui sont en cours ouvert ou fermé et sont par la suite de restauration, il seraient généralement annulent et la transaction serait beaucoup plus rapide, car il n’est pas bloquée chaque fois qu’il rencontre un ordre.  
  
 Pour plus d’informations, consultez [d’accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).
