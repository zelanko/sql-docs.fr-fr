---
title: Extension de SQL Server Profiler
titleSuffix: Azure Data Studio
description: Installer et utiliser l’extension de SQL Server Profiler (version préliminaire) pour Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: b883883cbe201de32020e86ca2cd38746caf46be
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63309697"
---
# <a name="sql-server-profiler-extension-preview"></a>Extension de SQL Server Profiler (version préliminaire)

L’extension de SQL Server Profiler (version préliminaire) fournit une solution de suivi SQL Server simple similaire à Profiler de SQL Server Management Studio (SSMS), à l’exception générée à l’aide d’événements étendus. SQL Server Profiler est très facile à utiliser et a des valeurs par défaut adéquates pour les configurations de suivi les plus courantes. L’expérience utilisateur est optimisé pour la navigation via des événements et l’affichage du texte Transact-SQL (T-SQL) associé. Le Profiler de serveur SQL pour Azure Data Studio suppose également les valeurs par défaut adéquates pour la collecte des activités de l’exécution de T-SQL avec un UX facile à utiliser. Cette extension est actuellement en version préliminaire.

**SQL Profiler-cas d’utilisation courants :**

- Exécuter pas à pas des requêtes posant problème afin d'en déterminer la cause.
- Détecter les requêtes s'exécutant lentement et diagnostiquer la cause du problème.
- Capturer la série d’instructions Transact-SQL qui mènent à un problème.
- Analyse des performances de SQL Server pour paramétrer les charges de travail.
- Mise en corrélation des compteurs de performances pour diagnostiquer des problèmes.


## <a name="install-the-sql-server-profiler-extension"></a>Installer l’extension de SQL Server Profiler

1. Pour ouvrir le Gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône des extensions ou **Extensions** dans le **vue** menu.
2. Sélectionner une extension disponible pour afficher ses détails.

   ![Gestionnaire d’extensions du profileur](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Sélectionnez l’extension souhaitée et **installer** il.
2. Sélectionnez **recharger** pour activer l’extension (uniquement obligatoire la première fois que vous installez une extension).

## <a name="start-profiler"></a>Démarrez Profiler

1. Pour commencer à Profiler, vous devez tout d’abord établir une connexion à un serveur dans l’onglet serveurs.
2. Après avoir établi une connexion, tapez **Alt + P** pour lancer Profiler.
3. Pour commencer à Profiler, tapez **Alt + S.** Vous pouvez maintenant commencer à voir les événements étendus.
    ![Gestionnaire d’extensions du profileur](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Pour arrêter de Profiler, tapez **Alt + S.** Ce raccourci clavier est un bouton bascule.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur Profiler et les événements étendus, consultez [événements étendus](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).





