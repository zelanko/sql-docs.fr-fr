---
title: Options (Page de requête d’exécution SQL Server-général) | Microsoft Docs
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
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionGeneral
ms.assetid: 3f8d59bc-3f97-4e5d-8b86-5ac670d20780
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2c08ee6ab08fe90ffc075ef3f1ee0fe638d1da4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167150"
---
# <a name="options-query-execution-sql-server-general-page"></a>Options (Page de requête d’exécution SQL Server-général)
  Cette page vous permet de spécifier les options d'exécution des requêtes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Les modifications de ces options sont appliquées uniquement aux nouvelles requêtes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour modifier les options relatives à une requête en cours, cliquez sur **Options de requête** dans le menu **Requête** ou cliquez avec le bouton droit dans une fenêtre Requête de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionnez **Options de requête**.  
  
## <a name="options"></a>Options  
 **SET ROWCOUNT**  
 La valeur par défaut 0 indique que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attend les résultats, tant que tous les résultats ne sont pas reçus. Spécifiez une valeur supérieure à 0 pour que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] arrête la requête après avoir obtenu le nombre de lignes spécifié. Pour désactiver cette option, de manière à renvoyer toutes les lignes, spécifiez SET ROWCOUNT 0.  
  
 **SET TEXTSIZE**  
 La valeur par défaut de 2 147 483 647 octets indique que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournira des champs de données complets jusqu'à la limite des champs de données `text` et `ntext`. Spécifiez un nombre inférieur pour limiter les résultats en cas de valeurs importantes. Les colonnes d'une taille supérieure au nombre spécifié sont tronquées.  
  
 **Délai d'exécution**  
 Définit la valeur par défaut dans la boîte de dialogue **Nouvelle connexion** . Utilisez cette zone de sélection numérique pour indiquer à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] le nombre de secondes à patienter avant d’annuler la requête. La valeur 0 indique un délai d'attente illimité ou pas de délai. Cette valeur est égale à 0 pour une nouvelle installation.  
  
 **Délimiteur de lot**  
 Tapez un mot à utiliser pour séparer les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] en traitements. La valeur par défaut est GO.  
  
 **Par défaut, ouvrir les nouvelles requêtes en Mode SQLCMD**  
 Activez cette case à cocher pour ouvrir les nouvelles requêtes en mode SQLCMD. Pour plus d’informations sur le mode SQLCMD, consultez [Modifier des scripts SQLCMD à l’aide de l’Éditeur de requête](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md).  
  
 Lorsque vous sélectionnez cette option, prenez en compte les limitations suivantes :  
  
-   IntelliSense dans l’Éditeur de requête du [!INCLUDE[ssDE](../includes/ssde-md.md)] est désactivé.  
  
-   L'Éditeur de requête ne s'exécutant pas à partir de la ligne de commande, vous ne pouvez pas passer de paramètres de ligne de commande tels que des variables.  
  
-   L'Éditeur de requête étant incapable de répondre aux invites de système d'exploitation, vous devez prendre soin de ne pas exécuter d'instructions interactives.  
  
 **Réinitialiser les valeurs par défaut**  
 Cliquez ici pour rétablir les valeurs par défaut d'origine de toutes les valeurs de cette page.  
  
## <a name="see-also"></a>Voir aussi  
 [sqlcmd Utility](../tools/sqlcmd-utility.md)  
  
  
