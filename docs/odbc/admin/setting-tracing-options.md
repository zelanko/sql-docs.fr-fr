---
title: Définition des Options de suivi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Analyzer tracing [ODBC]
- ODBC data source administrator [ODBC], tracing options
- tracing options [ODBC], ODBC data source administrator
ms.assetid: 44404a79-b716-4bc1-9ffb-70cd8239d237
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2ccf5afd559d4d3716c22b42665c516aa230fafe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198526"
---
# <a name="setting-tracing-options"></a>Définition des options de suivi
Le **suivi** onglet de la **administrateur de sources de données ODBC** boîte de dialogue vous permet de configurer la manière dont les appels de fonctions ODBC sont suivis.  
  
## <a name="how-tracing-works"></a>Le fonctionnement du suivi  
 Lorsque vous démarrez le suivi par le **suivi** onglet, le Gestionnaire de pilotes enregistrera tous les appels de fonction ODBC pour toutes les exécuter par la suite d’applications. Appels de fonction ODBC à partir d’applications qui s’exécutent avant le démarrage de suivi ne sont pas enregistrés. Appels de fonctions ODBC sont enregistrées dans un fichier journal que vous spécifiez.  
  
 Le suivi s’arrête uniquement après avoir cliqué sur **arrêter le traçage maintenant**. N’oubliez pas que, bien que le suivi est activé, le fichier journal continue d’augmenter et que cela affecte les performances de toutes vos applications ODBC.  
  
 Pour plus d’informations sur le suivi, consultez [suivi](../../odbc/reference/develop-app/tracing.md).  
  
### <a name="changes-in-odbc-tracing"></a>Modifications dans le traçage ODBC  
 Avant MDAC 2.7 SP2, le traçage ODBC est uniquement autorisé à se produire sur un ordinateur à l’échelle, dans lequel trace capture des détails exposés sur toutes les applications ODBC exécutées sous des identités. Cette partie le suivi de l’activité liée à ODBC qui peut-être se produire pour les processus créés ou exécuter pour le compte d’autres comptes d’utilisateurs locaux et les principaux de sécurité intégrés tels que le Service Local et Service réseau.  
  
 Par défaut, ODBC, le traçage utilise désormais le mode utilisateur unique. Si vous êtes un administrateur local, vous pouvez toutefois, toujours activer le suivi de l’ordinateur à l’aide de l’administrateur de sources de données ODBC.  
  
 Pour configurer le mode de suivi ODBC :  
  
1.  S’il est nécessaire, connectez-vous à l’aide d’un compte qui est membre du groupe Administrateurs Local.  
  
2.  À partir d’outils d’administration, ouvrez l’administrateur de sources de données ODBC.  
  
3.  Cliquez sur le **suivi** onglet.  
  
4.  Configurer le mode de suivi à l’aide de la **le suivi de l’ordinateur pour toutes les identités utilisateur** case à cocher :  
  
5.  Pour activer le suivi de l’ordinateur, sélectionnez la case à cocher.  
  
6.  Pour revenir au suivi par utilisateur, désactivez la case à cocher.  
  
7.  Cliquez sur **Appliquer**.  
  
> [!NOTE]  
>  Si vous avez déjà commencé le suivi dans un mode, vous devez arrêter le suivi et basculez vers l’autre mode pour le mode à être modifié avec succès.  
  
> [!IMPORTANT]  
>  Le suivi de l’ordinateur ne doit être activé que lorsque cela est nécessaire ; Sinon, elle doit rester désactivée.  
  
## <a name="visual-studio-analyzer-tracing"></a>Suivi de Visual Studio Analyzer  
  
> [!IMPORTANT]  
>  Prise en charge pour Visual Studio Analyzer a été supprimée à compter de 8 Windows (Visual Studio Analyzer a été inclus uniquement dans les versions antérieures de Visual Studio.). Pour un autre mécanisme de résolution des problèmes, utilisez le suivi.  
  
 Suivi de Visual Studio® Analyzer fournit des performances et des informations de débogage sur la couche ODBC. Tous les événements sortants seront déclenchés à l’interface de niveau supérieur pour présenter une image exacte que possible concernant temps passé dans les composants ODBC. Visual Studio Analyser requiert n’importe quelle source d’événement à s’inscrire durant la source est configurée. Pour plus d’informations sur ce type de traçage, consultez la documentation de Visual Studio.
