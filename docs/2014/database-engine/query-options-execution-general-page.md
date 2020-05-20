---
title: Exécution des options de requête (page général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.general.f1
ms.assetid: 858a0263-2f04-4692-b8bf-63e93c998ead
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f862f2067a1a85663754ab795822f2859b6c416a
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000599"
---
# <a name="query-options-execution-general-page"></a>Options de requête – Exécution (page Général)
  Cette page vous permet de spécifier les options d'exécution des requêtes [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour accéder à cette boîte de dialogue, cliquez avec le bouton droit sur le corps d’une fenêtre de l’éditeur de requête, puis cliquez sur **Options de requête**.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **SET ROWCOUNT**  
 La valeur par défaut 0 indique que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attend les résultats, tant que tous les résultats ne sont pas reçus. Spécifiez une valeur supérieure à 0 pour que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] arrête la requête après avoir obtenu le nombre de lignes spécifié. Pour désactiver cette option, de manière à renvoyer toutes les lignes, spécifiez SET ROWCOUNT 0.  
  
 **SET TEXTSIZE**  
 La valeur par défaut de 2 147 483 647 octets indique que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournira un champ de données complet jusqu'à la limite des champs de données `text`, `ntext`, `nvarchar(max)` et `varchar(max)`. Cela n'affecte pas le type de données XML. Spécifiez un nombre inférieur pour limiter les résultats en cas de valeurs importantes. Les colonnes d'une taille supérieure au nombre spécifié sont tronquées.  
  
 **Délai d’exécution**  
 Spécifie le nombre de secondes à attendre avant d'annuler la requête. La valeur 0 indique un délai d'attente illimité ou pas de délai.  
  
 **Délimiteur de traitement**  
 Tapez un mot à utiliser pour séparer les instructions Transact-SQL en traitements. La valeur par défaut est GO.  
  
 **Par défaut, ouvrir les nouvelles requêtes en mode SQLCMD**  
 Activez cette case à cocher pour ouvrir les nouvelles requêtes en mode SQLCMD. Cette case à cocher est visible uniquement lorsque la boîte de dialogue est ouverte via le menu **Outils** .  
  
 Lorsque vous sélectionnez cette option, prenez en compte les limitations suivantes :  
  
-   IntelliSense dans l’Éditeur de requête du [!INCLUDE[ssDE](../includes/ssde-md.md)] est désactivé.  
  
-   L'Éditeur de requête ne s'exécutant pas à partir de la ligne de commande, vous ne pouvez pas passer de paramètres de ligne de commande tels que des variables.  
  
-   L'Éditeur de requête étant incapable de répondre aux invites de système d'exploitation, vous devez prendre soin de ne pas exécuter d'instructions interactives.  
  
 **Rétablir les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  
