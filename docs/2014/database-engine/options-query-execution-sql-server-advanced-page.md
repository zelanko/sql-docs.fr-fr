---
title: 'Options (exécution de la requête : SQL Server : page avancé) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAdvanced
ms.assetid: 3ec788c7-22c3-4216-9ad0-81a168d17074
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 5323054b77ed26a3ada816f44c1bf6764ded931d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089371"
---
# <a name="options-query-executionsql-serveradvanced-page"></a>Options (Exécution de la requête : SQL Server : Page Avancé)
  Plusieurs options sont disponibles lors de l'utilisation de la commande SET. Cette page vous permet de spécifier une option **set** pour l'exécution des requêtes [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans l'éditeur de requête SQL Server. Elles n'ont aucun effet sur les autres éditeurs de code. Les modifications de ces options sont appliquées uniquement aux nouvelles requêtes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour modifier les options des requêtes en cours, cliquez sur **Options de requête** dans le menu **Requête** ou dans le menu contextuel de la fenêtre Requête de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Sous **Exécution**, cliquez sur **Avancé**. Pour plus d'informations sur chaque option, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Options  
 **SET NOCOUNT**  
 Ne retourne pas le nombre de lignes, comme message avec le jeu de résultats. Cette case à cocher est désactivée par défaut.  
  
 **SET NOEXEC**  
 N'exécute pas la requête. Cette case à cocher est désactivée par défaut.  
  
 **DÉFINIR PARSEONLY**  
 Vérifie la syntaxe de chaque requête, mais n'exécute pas les requêtes. Cette case à cocher est désactivée par défaut.  
  
 **DÉFINIR CONCAT_NULL_YIELDS_NULL**  
 Lorsque cette case à cocher est activée, les requêtes qui concatènent une valeur existante avec une valeur NULL, retournent toujours une valeur NULL comme résultat. Lorsque cette case à cocher est désactivée, une valeur existante concaténée avec une valeur NULL, retourne la valeur existante. Cette case à cocher est activée par défaut.  
  
 **SET ARITHABORT**  
 Si cette case à cocher est activée, lorsqu'une instruction INSERT, DELETE ou UPDATE rencontre une erreur arithmétique (dépassement de capacité, division par zéro ou erreur de domaine) au cours de l'évaluation de l'expression, le programme met fin à la requête ou au traitement. Lorsque cette case à cocher est désactivée, une valeur NULL est fournie pour cette valeur, si possible, la requête se poursuit et un message est inclus avec le résultat. Pour plus d’informations, consultez [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql). Cette case à cocher est activée par défaut.  
  
 **DÉFINIR SHOWPLAN_TEXT**  
 Lorsque cette case à cocher est activée, le plan de requête est retourné au format texte avec chaque requête. Cette case à cocher est désactivée par défaut.  
  
 **DÉFINIR L’HEURE DES STATISTIQUES**  
 Lorsque cette case à cocher est activée, les statistiques de temps sont retournées avec chaque requête. Cette case à cocher est désactivée par défaut.  
  
 **DÉFINIR LES STATISTIQUES D’E/S**  
 Lorsque cette case à cocher est activée, les statistiques d'entrée/sortie sont retournées avec chaque requête. Cette case à cocher est désactivée par défaut.  
  
 **SET TRANSACTION ISOLATION LEVEL**  
 Le niveau d'isolation des transactions READ COMMITTED est défini par défaut. Pour plus d’informations, consultez [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql). Le niveau d'isolation des transactions SNAPSHOT n'est pas disponible. Pour utiliser l'isolation SNAPSHOT, ajoutez l'instruction [!INCLUDE[tsql](../includes/tsql-md.md)] suivante :  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 **SET DEADLOCK PRIORITY**  
 La valeur par défaut de Normal permet à chaque requête de disposer de la même priorité lorsqu'un blocage se produit. Sélectionnez une priorité Basse, si vous voulez que cette requête perde tout conflit de blocage et soit sélectionnée comme requête à interrompre.  
  
 **SET LOCK TIMEOUT**  
 La valeur par défaut -1 indique que les verrous sont maintenus tant que les transactions ne sont pas achevées. Une valeur égale à 0 signifie que l'instruction n'attendra pas et qu'elle retournera un message dès qu'un verrou sera localisé. Spécifiez une valeur supérieure à 0 milliseconde pour mettre fin à une transaction si les verrous de cette transaction doivent être maintenus plus longtemps que cette valeur.  
  
 **SET QUERY_GOVERNOR_COST_LIMIT**  
 Utilisez l'option **QUERY_GOVERNOR_COST_LIMIT** pour spécifier une limite supérieure de durée d'exécution d'une requête. Le coût d'une requête correspond à la durée (en secondes) estimée nécessaire à l'exécution complète d'une requête dans une configuration matérielle donnée. Une valeur par défaut égale à 0 indique une durée d'exécution illimitée d'une requête.  
  
 **Supprimer les en-têtes de message de fournisseur**  
 Lorsque cette case à cocher est activée, les messages d'état provenant du fournisseur (tel que le fournisseur SQLClient) ne sont pas affichés. Cette case à cocher est activée par défaut. Désactivez cette case à cocher pour afficher les messages du fournisseur lors de la résolution des problèmes en cas d'échec des requêtes au niveau du fournisseur.  
  
 **Déconnecter après l'exécution de la requête**  
 Lorsque cette case à cocher est activée, il est mis fin à la connexion à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] une fois la requête terminée. Cette case à cocher est désactivée par défaut.  
  
 **Rétablir les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  
