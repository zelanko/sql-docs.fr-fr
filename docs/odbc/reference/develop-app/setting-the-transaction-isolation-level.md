---
title: Définition du niveau d’isolation de la transaction | Microsoft Docs
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
ms.openlocfilehash: e59db823f8b84edfb5c92f2d142c8238449e3323
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107579"
---
# <a name="setting-the-transaction-isolation-level"></a>Définition du niveau d’isolation des transactions
Pour définir le niveau d’isolation de la transaction, une application utilise l’attribut de connexion SQL_ATTR_TXN_ISOLATION. Si la source de données ne prend pas en charge le niveau d’isolation demandé, le pilote ou la source de données peut définir un niveau supérieur. Pour déterminer les niveaux d’isolation des transactions pris en charge par une source de données et le niveau d’isolation par défaut, une application appelle **SQLGetInfo** avec les options SQL_TXN_ISOLATION_OPTION et SQL_DEFAULT_TXN_ISOLATION, respectivement.  
  
 Les niveaux d’isolation des transactions les plus élevés offrent la meilleure protection de l’intégrité des données de la base de données. Les transactions sérialisables sont garanties comme non affectées par d’autres transactions et, par conséquent, garantissent l’intégrité de la base de données.  
  
 Toutefois, un niveau d’isolation des transactions plus élevé peut entraîner une baisse des performances, car cela augmente le risque que l’application ait besoin d’attendre la libération de verrous sur les données. Une application peut spécifier un niveau d’isolation inférieur pour améliorer les performances dans les cas suivants :  
  
-   Lorsqu’il peut être garanti qu’aucune autre transaction ne peut interférer avec les transactions d’une application. Cette situation se produit uniquement dans des circonstances limitées, par exemple lorsqu’une personne d’une petite entreprise conserve des fichiers dBASE qui contiennent des données de personnel sur un ordinateur et ne partage pas ces fichiers.  
  
-   Lorsque la vitesse est plus importante que la précision et que des erreurs sont susceptibles d’être mineures. Supposons, par exemple, qu’une entreprise effectue de nombreuses petites ventes et que les ventes volumineuses soient rares. Une transaction qui estime la valeur totale de tous les ventes ouvertes peut utiliser en toute sécurité le niveau d’isolation lecture non validée. Bien que la transaction inclue les commandes qui sont ouvertes ou fermées et qui sont ensuite restaurées, elles s’annulent généralement mutuellement et la transaction est beaucoup plus rapide, car elle n’est pas bloquée à chaque fois qu’elle rencontre une telle commande.  
  
 Pour plus d’informations, consultez [accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).
