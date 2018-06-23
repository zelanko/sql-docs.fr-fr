---
title: Options de requête – exécution (Page ANSI) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
caps.latest.revision: 23
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 41c8957ebd2dfb77b13803945c210d6a09f1e874
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039162"
---
# <a name="query-options-execution-ansi-page"></a>Options de requête (page ANSI)
  Utilisez cette page pour spécifier si [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] exécute les requêtes avec l’ensemble ou une partie des paramètres spécifiés dans la norme ISO (ANSI).  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **SET ANSI_DEFAULTS**  
 Sélectionne tous les paramètres ISO par défaut. Par défaut, cette zone n'est pas disponible car seuls certains des paramètres ISO sont configurés.  
  
 **SET QUOTED_IDENTIFIER**  
 Place les identificateurs d'objets entre guillemets. Cette option est activée par défaut.  
  
 **SET ANSI_NULL_DFLT_ON**  
 Autorise les valeurs NULL pour tous les types de données définis par l’utilisateur ou les colonnes non explicitement définies comme NOTNULL lors d’une instruction CREATE TABLE ou ALTER TABLE (état par défaut). Cette option est activée par défaut.  
  
 **SET IMPLICIT_TRANSACTIONS**  
 Cette option est désactivée par défaut.  
  
 **SET CURSOR_CLOSE_ON_COMMIT**  
 Ferme automatiquement tous les curseurs ouverts (conformément à la norme ISO) lors de la validation d'une transaction. Lorsque cette option est désactivée (OFF), les curseurs restent ouverts d'une transaction à l'autre, ne se fermant que lors de la fermeture de la connexion ou sur demande explicite. Cette option est désactivée par défaut.  
  
 **SET ANSI_PADDING**  
 Contrôle le mode de stockage dans la colonne des valeurs dont la longueur est inférieure à la taille définie pour la colonne et de celles contenant des espaces à droite pour les données de type **char**, **varchar**, **binary**et **varbinary** . Cette valeur affecte uniquement la définition de nouvelles colonnes. Une fois la colonne créée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stocke les valeurs en fonction du paramètre en vigueur lors de la création de la colonne. Les colonnes existantes ne sont pas affectées par toute modification ultérieure du paramètre. Cette case à cocher est activée par défaut.  
  
 **SET ANSI_WARNINGS**  
 Spécifie le comportement conforme à la norme ISO pour plusieurs conditions d'erreur :  
  
-   Lorsque cette case à cocher est activée, si des valeurs de type NULL apparaissent dans des fonctions d'agrégation (telles que SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP ou COUNT), le système génère un message d'avertissement. Lorsque la valeur est **OFF**, aucun avertissement n'est émis.  
  
-   Lorsque cette case à cocher est désactivée, les erreurs de division par zéro et de dépassement arithmétique provoquent l'annulation de l'instruction et l'émission d'un message d'erreur. Lorsque la valeur est OFF, les erreurs de division par zéro et de dépassement arithmétique entraînent le renvoi de valeurs NULL. Une erreur de division par zéro ou de dépassement arithmétique provoque le renvoi de valeurs NULL si une instruction INSERT ou UPDATE est tentée sur une colonne de type character, Unicode ou binary contenant une nouvelle valeur dont la longueur est supérieure à la taille maximale de la colonne. Conformément à la norme ISO, si l’option **SET ANSI_WARNINGS** est activée (valeur ON), l’opération INSERT ou UPDATE est annulée. Les espaces de fin sont ignorés dans des colonnes character et les zéros à droite sont ignorés dans les colonnes binary. Lorsque la valeur est définie à OFF, les données sont tronquées de façon à correspondre à la taille de la colonne, et l'instruction s'exécute correctement.  
  
 Cette option est activée par défaut.  
  
 **SET ANSI_NULLS**  
 Spécifie le comportement conforme à la norme ISO, des opérateurs d'égalité (`=`) et de différence (`<>`), lorsqu'ils sont utilisés avec des valeurs NULL. Conformément à la norme ISO, quand **SET ANSI_NULLS** est sélectionné, toutes les comparaisons effectuées sur une valeur NULL retournent la valeur UNKNOWN. Quand **SET ANSI_NULLS** n’est pas sélectionné, les comparaisons de toutes les données par rapport à une valeur NULL sont vraies (TRUE) si la valeur des données est NULL. Cette option est activée par défaut.  
  
 **Réinitialiser les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  