---
title: SQL Operations Studio (version préliminaire) extension de SQL Server Profiler | Microsoft Docs
description: Extension de SQL Server Profiler pour SQL Operations Studio (version préliminaire)
ms.custom: tools|sos
ms.date: 07/19/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 190d54a4525a476b2c42c22d447264a1d95e7bc4
ms.sourcegitcommit: 4b21840f20195d70f255465666f7b409ba839d18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39147014"
---
# <a name="sql-server-profiler-extension"></a>Extension de SQL Server Profiler

Le Profiler de serveur SQL extension fournit une solution de suivi SQL Server simple similaire à Profiler de SQL Server Management Studio (SSMS), à l’exception générée à l’aide de XEvents. SQL Server Profiler est très facile à utiliser et a des valeurs par défaut adéquates pour les configurations de suivi les plus courantes. L’expérience utilisateur est optimisé pour la navigation via des événements et l’affichage du texte Transact-SQL (T-SQL) associé. Le Profiler de serveur SQL pour SQL Operations Studio suppose également les valeurs par défaut adéquates pour la collecte des activités de l’exécution de T-SQL avec un UX facile à utiliser.

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





