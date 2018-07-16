---
title: Options de requête d’exécution (Page avancée) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 548f8a0dd6a8c24c91144598f649e3bc564e614c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293039"
---
# <a name="query-options-execution-advanced-page"></a>Options Exécution de la requête (page Avancé)
  Différentes options sont disponibles à l'aide de l'instruction **SET** . Cette page vous permet de spécifier une option **set** pour exécuter les requêtes Microsoft SQL Server. Pour des informations détaillées sur chacune de ces options, consultez la documentation en ligne de SQL Server.  
  
 **SET NOCOUNT**  
 Ne retourne pas le nombre de lignes, comme message avec le jeu de résultats. Cette option est désactivée par défaut.  
  
 **SET NOEXEC**  
 N'exécute pas la requête. Cette option est désactivée par défaut.  
  
 **SET PARSEONLY**  
 Vérifie la syntaxe de chaque requête, mais n'exécute pas les requêtes. Cette option est désactivée par défaut.  
  
 **SET CONCAT_NULL_YIELDS_NULL**  
 Lorsque cette case à cocher est activée, les requêtes qui concatènent une valeur existante avec une valeur `NULL`, retournent toujours une valeur `NULL` comme résultat. Lorsque cette case à cocher est désactivée, une valeur existante concaténée avec une valeur `NULL`, retourne la valeur existante. Cette option est activée par défaut.  
  
 **SET ARITHABORT**  
 Si cette case à cocher est activée, lorsqu'une instruction `INSERT`, `DELETE` ou `UPDATE` rencontre une erreur arithmétique (dépassement de capacité, division par zéro ou erreur de domaine) au cours de l'évaluation de l'expression, le programme met fin à la requête ou au traitement. Lorsque cette case à cocher est désactivée, une valeur `NULL` est fournie pour cette valeur, si possible, la requête se poursuit et un message est inclus avec le résultat. Consultez la documentation en ligne pour une description plus complète de ce comportement. Cette option est activée par défaut.  
  
 **SET SHOWPLAN_TEXT**  
 Lorsque cette case à cocher est activée, le plan de requête est retourné sous forme de texte avec chaque requête. Cette option est désactivée par défaut.  
  
 **SET STATISTICS TIME**  
 Lorsque cette case à cocher est activée, les statistiques de temps sont retournées avec chaque requête. Cette option est désactivée par défaut.  
  
 **SET STATISTICS IO**  
 Lorsque cette case à cocher est activée, les statistiques d'entrée/sortie (E/S) sont retournées avec chaque requête. Cette option est désactivée par défaut.  
  
 **SET TRANSACTION ISOLATION LEVEL**  
 Le niveau d'isolation des transactions READ COMMITTED est défini par défaut. Pour plus d’informations, consultez [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql). Le niveau d'isolation des transactions SNAPSHOT n'est pas disponible. Pour utiliser l'isolation SNAPSHOT, ajoutez l'instruction [!INCLUDE[tsql](../includes/tsql-md.md)] suivante :  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 **PRIORITÉ DE BLOCAGE DE JEU**  
 La valeur par défaut **Normal** permet à chaque requête de disposer de la même priorité lorsqu'un blocage se produit. Sélectionnez une priorité Basse dans la liste déroulante, si vous voulez que cette requête perde tout conflit de blocage et soit sélectionnée comme requête à interrompre.  
  
 **DÉLAI D’ATTENTE DU VERROU DE JEU**  
 La valeur par défaut -1 indique que les verrous sont maintenus tant que les transactions ne sont pas achevées. Une valeur égale à 0 signifie que l'instruction n'attendra pas et qu'elle retournera un message dès qu'un verrou sera localisé. Spécifiez une valeur supérieure à 0 milliseconde pour mettre fin à une transaction si les verrous de cette transaction doivent être maintenus plus longtemps que cette valeur.  
  
 **SET QUERY_GOVERNOR_COST_LIMIT**  
 Utilisez l'option **SET QUERY_GOVERNOR_COST_LIMIT** pour spécifier une limite supérieure de durée d'exécution d'une requête. Le coût d'une requête correspond à la durée (en secondes) estimée nécessaire à l'exécution complète d'une requête dans une configuration matérielle donnée. La valeur par défaut 0 indique une durée d'exécution illimitée pour une requête.  
  
 **Supprimer les en-têtes de message de fournisseur**  
 Lorsque cette case à cocher est activée, les messages d'état provenant du fournisseur (tel que le fournisseur OLE DB) ne sont pas affichés. Cette case à cocher est activée par défaut. Désactivez cette case à cocher pour afficher les messages du fournisseur lors de la résolution des problèmes en cas d'échec des requêtes au niveau du fournisseur.  
  
 **Déconnecter après l’exécution de la requête**  
 Lorsque cette case à cocher est activée, il est mis fin à la connexion à SQL Server une fois la requête terminée. Cette option est désactivée par défaut.  
  
 **Réinitialiser les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  
