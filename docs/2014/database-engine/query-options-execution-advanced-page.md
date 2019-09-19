---
title: Exécution d’options de requête (page avancé) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: ''
ms.custom: ''
ms.date: 09/03/2019
ms.openlocfilehash: 4530d07ceb284f6f7c5a795836b979e846562f40
ms.sourcegitcommit: b016c01c47bc08351d093a59448d895cc170f8c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118107"
---
# <a name="query-options-execution-advanced-page"></a>Options Exécution de la requête (page Avancé)

  Différentes options sont disponibles à l'aide de l'instruction **SET** . Utilisez cette page pour spécifier une option **Set** pour exécuter Microsoft SQL Server des requêtes. Pour des informations détaillées sur chacune de ces options, consultez la documentation en ligne de SQL Server.
  
**Set NOcount** Ne retourne pas le nombre de lignes, sous la forme d’un message avec le jeu de résultats. Cette option est désactivée par défaut.

**Set NOexec** N’exécute pas la requête. Cette option est désactivée par défaut.

**définir PARSEONLY** Vérifie la syntaxe de chaque requête, mais n’exécute pas les requêtes. Cette option est désactivée par défaut.  

**définir CONCAT_NULL_YIELDS_NULL** Lorsque cette case à cocher est activée, les requêtes qui concatènent une valeur existante `NULL`avec un, retournent toujours une `NULL` valeur comme résultat. Lorsque cette case à cocher est désactivée, une valeur existante concaténée avec une valeur `NULL`, retourne la valeur existante. Cette option est activée par défaut.

**SET ARITHABORT** Lorsque cette case à cocher est activée, `INSERT`lorsqu' `DELETE` une `UPDATE` instruction, ou rencontre une erreur arithmétique (dépassement de capacité, Division par zéro ou erreur de domaine) lors de l’évaluation de l’expression, la requête ou le traitement est terminé. Lorsque cette case à cocher est désactivée, une valeur `NULL` est fournie pour cette valeur, si possible, la requête se poursuit et un message est inclus avec le résultat. Consultez la documentation en ligne pour une description plus complète de ce comportement. Cette option est activée par défaut.
  
**SET SHOWPLAN_TEXT** Lorsque cette case à cocher est activée, le plan de requête est retourné sous forme de texte avec chaque requête. Cette option est désactivée par défaut.
  
**définir l’heure des statistiques** Lorsque cette case à cocher est activée, les statistiques de temps sont retournées avec chaque requête. Cette option est désactivée par défaut.
  
**définir les statistiques d’e/s** Lorsque cette case à cocher est activée, les statistiques relatives à l’entrée/sortie (e/s) sont retournées avec chaque requête. Cette option est désactivée par défaut.
  
**définir le niveau d’isolation** de la transaction Le niveau d’isolation de la transaction READ COMMITTED est défini par défaut. Pour plus d’informations, consultez [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql). Le niveau d’isolation de la transaction d’instantané n’est pas disponible. Pour utiliser l'isolation SNAPSHOT, ajoutez l'instruction [!INCLUDE[tsql](../includes/tsql-md.md)] suivante :
  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
  GO
  ```

**définir la priorité de blocage** La valeur par défaut **normal** permet à chaque requête d’avoir la même priorité lorsqu’un blocage se produit. Sélectionnez une priorité Basse dans la liste déroulante, si vous voulez que cette requête perde tout conflit de blocage et soit sélectionnée comme requête à interrompre.

**définir le délai de verrouillage** La valeur par défaut-1 indique que les verrous sont maintenus jusqu’à ce que les transactions soient terminées. Une valeur égale à 0 signifie que l'instruction n'attendra pas et qu'elle retournera un message dès qu'un verrou sera localisé. Spécifiez une valeur supérieure à 0 milliseconde pour mettre fin à une transaction si les verrous de cette transaction doivent être maintenus plus longtemps que cette valeur.

**définir QUERY_GOVERNOR_COST_LIMIT** Utilisez l’option limite de coût de l' **administrateur de requêtes** pour spécifier une limite supérieure de la période pendant laquelle une requête peut s’exécuter. Le coût d'une requête correspond à la durée (en secondes) estimée nécessaire à l'exécution complète d'une requête dans une configuration matérielle donnée. La valeur par défaut 0 indique une durée d'exécution illimitée pour une requête.

**Supprimer les en-têtes de message de fournisseur** Lorsque cette case à cocher est activée, les messages d’État du fournisseur (tels que le fournisseur OLE DB) ne sont pas affichés. Cette case à cocher est activée par défaut. Désactivez cette case à cocher pour afficher les messages du fournisseur lors de la résolution des problèmes en cas d'échec des requêtes au niveau du fournisseur.

**Déconnecter après l’exécution de la requête** Lorsque cette case à cocher est activée, la connexion à SQL Server se termine une fois la requête terminée. Cette option est désactivée par défaut.

**Afficher l’heure d’achèvement** Permet d’imprimer l’heure à laquelle l’exécution de la requête s’est terminée après les résultats de la requête ou dans l’onglet messages.

**Protocole d’attestation pour les enclaves vbs pour Always Encrypted** Vous permet de définir un protocole d’attestation pour les enclaves de sécurité basée sur la virtualisation (VBS) utilisées par les Always Encrypted avec des enclaves sécurisées. 

  Les protocoles d’attestation actuellement pris en charge sont les suivants :

  * Host Guardian service : protocole d’attestation utilisant le service Windows Host Guardian (SGH).

Pour plus d’informations, consultez [Always Encrypted avec les enclaves sécurisées](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) et l' [attestation d’enclave sécurisée](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation).

**Rétablir les valeurs par défaut** Rétablit toutes les valeurs par défaut initiales des options de cette page.
