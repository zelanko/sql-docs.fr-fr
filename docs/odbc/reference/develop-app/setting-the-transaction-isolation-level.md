---
title: Définir le niveau d’isolement des transactions (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80401b276355a47469355cb6921d768d168398ae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299809"
---
# <a name="setting-the-transaction-isolation-level"></a>Définition du niveau d’isolation des transactions
Pour définir le niveau d’isolement des transactions, une application utilise l’attribut de connexion SQL_ATTR_TXN_ISOLATION. Si la source de données ne prend pas en charge le niveau d’isolement demandé, le conducteur ou la source de données peut établir un niveau plus élevé. Pour déterminer quels niveaux d’isolement des transactions une source de données prend en charge et quel est le niveau d’isolement par défaut, une application appelle **SQLGetInfo** avec les options SQL_TXN_ISOLATION_OPTION et SQL_DEFAULT_TXN_ISOLATION, respectivement.  
  
 Des niveaux plus élevés d’isolement des transactions offrent le plus de protection pour l’intégrité des données de base de données. Les transactions sérialisables sont garanties d’être non affectées par d’autres transactions et donc garanties de maintenir l’intégrité de la base de données.  
  
 Cependant, un niveau plus élevé d’isolement des transactions peut entraîner un ralentissement des performances, car il augmente les chances que l’application devra attendre que les verrous sur les données soient publiés. Une demande peut spécifier un niveau d’isolement inférieur pour augmenter le rendement dans les cas suivants :  
  
-   Lorsqu’il est possible de garantir qu’il n’existe aucune autre transaction qui pourrait interférer avec les transactions d’une application. Cette situation ne se produit que dans des circonstances limitées, par exemple lorsqu’une personne d’une petite entreprise tient des fichiers dBASE qui contiennent des données du personnel sur un ordinateur et ne partage pas ces fichiers.  
  
-   Lorsque la vitesse est plus critique que la précision et que toute erreur est susceptible d’être faible. Supposons, par exemple, qu’une entreprise réalise de nombreuses petites ventes et que les grandes ventes sont rares. Une transaction qui estime la valeur totale de toutes les ventes ouvertes peut utiliser en toute sécurité le niveau d’isolement Read Uncommitted. Bien que la transaction inclue des commandes qui sont ouvertes ou fermées et qui sont par la suite annulées, celles-ci s’annuleraient généralement les unes les autres et la transaction serait beaucoup plus rapide parce qu’elle n’est pas bloquée chaque fois qu’elle fait l’objet d’une telle commande.  
  
 Pour plus d’informations, voir [Concordurrency Optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).
