---
title: Options (éditeur de texte-Transact-SQL-IntelliSense) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 5472e7d0c910c03f49425c263293fd721320eba9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844348"
---
# <a name="options-text-editor-transact-sql-intellisense"></a>Options (Text Editor-Transact-SQL-IntelliSense)
  La boîte de dialogue **Options** vous permet de modifier les paramètres IntelliSense pour l'éditeur de requête du [!INCLUDE[ssDE](../includes/ssde-md.md)] . Pour accéder à ces paramètres, dans le menu **Outils** , cliquez sur **Options**, développez le dossier **Éditeur de texte** , puis le dossier **Transact-SQL** , et cliquez sur **Avancés**.  
  
## <a name="transact-sql-intellisense-settings"></a>Paramètres IntelliSense Transact-SQL  
 Spécifie les options IntelliSense pour l'éditeur de [!INCLUDE[ssDE](../includes/ssde-md.md)] requête du moteur de base de données.  
  
### <a name="enable-intellisense"></a>Activer IntelliSense  
 Active les fonctionnalités IntelliSense. Lorsque cette case à cocher n'est pas activée, les options IntelliSense spécifiques ne sont pas disponibles. Par défaut, cette case à cocher est activée.  
  
 **Souligner les erreurs**  
 Identifie les erreurs syntaxiques et sémantiques dans les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] dans la fenêtre de requête. Les erreurs et les avertissements apparaissent en rouge. Les erreurs et les avertissements sont uniquement pris en charge pour les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] pour lesquelles IntelliSense a été implémenté. Par défaut, cette case à cocher est activée.  
  
 **Instructions de plan**  
 Active le mode Plan lorsqu'un fichier est ouvert. Cela entraîne la création de blocs réductibles de code [!INCLUDE[tsql](../includes/tsql-md.md)] . Par défaut, cette case à cocher est activée.  
  
 **Taille de script maximale**  
 Spécifie la taille à laquelle les fonctionnalités IntelliSense sont désactivées. Si un script dépasse la taille spécifiée, un message d'avertissement est émis. Toutes les fonctionnalités IntelliSense, à l'exception du codage en couleurs, sont désactivées pour cette fenêtre d'éditeur. IntelliSense est réactivé lorsque suffisamment de texte est supprimé pour faire passer la taille du script sous la limite. L'activation d'IntelliSense pour les scripts volumineux peut réduire les performances sur les ordinateurs lents. Les tailles autorisées sont 100 Ko, 500 Ko, 1 Mo, 2 Mo et Illimité. La valeur par défaut est 1 Mo.  
  
 **Casse des noms de fonctions intégrées**  
 Indique si les noms de fonctions [!INCLUDE[tsql](../includes/tsql-md.md)] intégrées incluses dans les listes de saisie semi-automatique utilisent des lettres majuscules, telles que DATEADD, ou des lettres minuscules, telles que dateadd. Sélectionnez l'option qui correspond le mieux aux conventions de codage [!INCLUDE[tsql](../includes/tsql-md.md)] que vous utilisez.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage d’IntelliSense &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
