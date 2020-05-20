---
title: Options (exécution de la requête-SQL Server-page ANSI) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAnsi
ms.assetid: 0f4c6887-0562-417e-806c-b5cffb1e7c5c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 23e46eaf73be4f14e90065627379bb778525051a
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000839"
---
# <a name="options-query-execution-sql-server-ansi-page"></a>Options (exécution de la requête-SQL Server-page ANSI)
  Ensemble, ces options SET ANSI (ISO) définissent l'environnement de traitement des requêtes pour la durée de la requête de l'utilisateur, de l'exécution d'un déclencheur ou d'une procédure stockée. Toutefois, ces options SET ne contiennent pas toutes les options requises pour assurer la conformité à la norme ISO. Utilisez cette page pour spécifier que [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] exécute les requêtes à l’aide de l’ensemble ou d’une partie des paramètres spécifiés dans la norme ISO. Les modifications apportées à ces options sont appliquées uniquement aux nouvelles requêtes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour modifier les options des requêtes en cours, cliquez sur **options de requête** dans le menu **requête** ou cliquez avec le bouton droit dans la fenêtre de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requête et sélectionnez **options de requête**. Dans la boîte de dialogue **Options de requête** , sous **Exécution**, cliquez sur **ANSI**.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **SET ANSI_DEFAULTS**  
 Activez cette case à cocher pour sélectionner tous les paramètres ISO par défaut. Les options ISO ne sont pas toutes sélectionnées par défaut.  
  
 **SET QUOTED_IDENTIFIER**  
 Lorsque cette case à cocher est activée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] suit les règles ISO relatives aux guillemets délimitant les identificateurs et les chaînes littérales. Les identificateurs entre guillemets peuvent être des mots clés Transact-SQL réservés ou contenir des caractères qui ne sont généralement pas autorisés dans les règles syntaxiques Transact-SQL se rapportant aux identificateurs. Cette case à cocher est activée par défaut.  
  
 **SET ANSI_NULL_DFLT_ON**  
 Lorsque cette option est activée, tous les types de données définis par l'utilisateur ou les colonnes qui ne sont pas définies explicitement comme NOT NULL dans une instruction CREATE TABLE ou ALTER TABLE autorisent, par défaut, les valeurs NULL. Cette case à cocher est activée par défaut.  
  
 **SET IMPLICIT_TRANSACTIONS**  
 Lorsque cette case à cocher est activée, SET IMPLICIT_TRANSACTIONS met la connexion en mode de transaction implicite. Lorsque la case à cocher est désactivée, la connexion revient en mode de validation automatique. Pour passer en revue les instructions qui démarrent une transaction implicite quand elles sont sélectionnées, consultez [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-implicit-transactions-transact-sql). Cette case à cocher est désactivée par défaut.  
  
 **SET CURSOR_CLOSE_ON_COMMIT**  
 Lorsque cette case à cocher est activée, tous les curseurs ouverts sont fermés automatiquement (conformément à ISO) lors de la validation d'une transaction. Lorsque cette option est désactivée, les curseurs restent ouverts d'une transaction à l'autre, ne se fermant que lors de la fermeture de la connexion ou sur demande explicite. Cette case à cocher est désactivée par défaut.  
  
 **SET ANSI_PADDING**  
 Contrôle la façon dont la colonne stocke les noms de valeurs dont la longueur est inférieure à la taille définie pour la colonne et les valeurs contenant des espaces de fin pour les données de type **char**, **varchar**, **binary**et **varbinary** . Cette valeur affecte uniquement la définition de nouvelles colonnes. Une fois la colonne créée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stocke les valeurs en fonction du paramètre en vigueur lors de la création de la colonne. Les colonnes existantes ne sont pas affectées par toute modification ultérieure du paramètre. Cette case à cocher est activée par défaut.  
  
 **SET ANSI_WARNINGS**  
 Spécifie le comportement conforme à la norme ISO pour plusieurs conditions d'erreur :  
  
-   Lorsque cette case à cocher est activée, si des valeurs de type NULL apparaissent dans des fonctions d'agrégation (telles que SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP ou COUNT), le système génère un message d'avertissement. Lorsque cette case à cocher est désactivée, aucun avertissement n'est émis.  
  
-   Lorsque cette case à cocher est activée, les erreurs de division par zéro et de dépassement arithmétique provoquent l'annulation de l'instruction et l'émission d'un message d'erreur. Lorsque la valeur est OFF, les erreurs de division par zéro et de dépassement arithmétique entraînent le renvoi de valeurs NULL. Une erreur de division par zéro ou de dépassement arithmétique provoque le retour de valeurs NULL si une opération INSERT ou UPDATE est tentée sur une colonne de type **character**, **Unicode** ou **binary** contenant une nouvelle valeur dont la longueur est supérieure à la taille maximale de la colonne. Conformément à la norme ISO, si l'option SET ANSI_WARNINGS est activée, l'opération INSERT ou UPDATE est annulée. Les espaces blancs sont ignorés dans des colonnes de type caractère et les zéros sont ignorés dans les colonnes de type binaire. Lorsque la valeur est définie à OFF, les données sont tronquées de façon à correspondre à la taille de la colonne, et l'instruction s'exécute correctement.  
  
 Cette case à cocher est activée par défaut.  
  
 **SET ANSI_NULLS**  
 -   Spécifie le comportement conforme à la norme ISO pour les opérateurs de comparaison égal à (=) et différent de (<>), lorsqu'ils sont utilisés avec des valeurs Null. Conformément à la norme ISO, lorsque l'option SET ANSI_NULLS est activée, toutes les comparaisons effectuées par rapport à une valeur NULL renvoient la valeur UNKNOWN (inconnu). Lorsque l'option SET ANSI_NULLS n'est pas activée, toutes les comparaisons effectuées par rapport à une valeur NULL renvoient la valeur TRUE. Cette case à cocher est activée par défaut.  
  
 **Rétablir les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  
