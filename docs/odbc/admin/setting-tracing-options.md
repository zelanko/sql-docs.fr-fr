---
title: Définition des options de suivi | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 21bee5d903459423a134389e62db844f5f63c9c1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307193"
---
# <a name="setting-tracing-options"></a>Définition des options de suivi
L’onglet **suivi** de la boîte de dialogue **administrateur de sources de données ODBC** vous permet de configurer la façon dont les appels de fonction ODBC sont suivis.  
  
## <a name="how-tracing-works"></a>Fonctionnement du suivi  
 Lorsque vous démarrez le suivi à partir de l’onglet **suivi** , le gestionnaire de pilotes enregistre tous les appels de fonction ODBC pour toutes les applications d’exécution ultérieures. Les appels de fonction ODBC à partir d’applications qui s’exécutent avant le démarrage du suivi ne sont pas journalisés. Les appels de fonction ODBC sont enregistrés dans un fichier journal que vous spécifiez.  
  
 Le suivi s’arrête uniquement lorsque vous cliquez sur **arrêter le suivi maintenant**. N’oubliez pas que si le suivi est activé, le fichier journal continue d’augmenter et cela affecte les performances de toutes vos applications ODBC.  
  
 Pour plus d’informations sur le suivi, consultez [traçage](../../odbc/reference/develop-app/tracing.md).  
  
### <a name="changes-in-odbc-tracing"></a>Modifications du traçage ODBC  
 Avant MDAC 2,7 SP2, le suivi ODBC était uniquement autorisé à se produire à l’échelle de l’ordinateur, dans lequel trace capture des détails sur toutes les applications ODBC s’exécutant sous des identités. Cela inclut le suivi pour les activités liées à ODBC qui peuvent se produire pour les processus créés ou exécutés pour le compte d’autres comptes d’utilisateurs locaux et des principaux de sécurité intégrés, tels que le service local et le service réseau.  
  
 Par défaut, le traçage ODBC utilise désormais le mode par utilisateur. Toutefois, si vous êtes administrateur local, vous pouvez toujours activer le suivi à l’ensemble de l’ordinateur à l’aide de l’administrateur de la source de données ODBC.  
  
 Pour configurer le mode de traçage ODBC :  
  
1.  Si nécessaire, connectez-vous à l’aide d’un compte qui est membre du groupe Administrateurs local.  
  
2.  Dans outils d’administration, ouvrez l’administrateur de la source de données ODBC.  
  
3.  Cliquez sur l’onglet **suivi** .  
  
4.  Configurez le mode de suivi à l’aide de la case à cocher **suivi au niveau de l’ordinateur pour toutes les identités utilisateur** :  
  
5.  Pour activer le suivi à l’ensemble de l’ordinateur, activez la case à cocher.  
  
6.  Pour revenir au suivi par utilisateur, désactivez la case à cocher.  
  
7.  Cliquez sur **Appliquer**.  
  
> [!NOTE]  
>  Si vous avez déjà démarré le suivi dans un mode, vous devez arrêter le suivi et basculer vers l’autre mode pour que le mode soit correctement modifié.  
  
> [!IMPORTANT]  
>  Le suivi au niveau de l’ordinateur ne doit être activé que si nécessaire. dans le cas contraire, il doit être désactivé.  
  
## <a name="visual-studio-analyzer-tracing"></a>Suivi des Visual Studio Analyzer  
  
> [!IMPORTANT]  
>  La prise en charge de Visual Studio Analyzer a été supprimée depuis Windows 8 (Visual Studio Analyzer n’était inclus que dans les versions antérieures de Visual Studio). Pour un autre mécanisme de résolution des problèmes, utilisez le suivi des enchères.  
  
 Le suivi de l’analyseur de® Visual Studio fournit des informations sur les performances et le débogage de la couche ODBC. Tous les événements sortants seront déclenchés au niveau de l’interface de niveau supérieur pour présenter une image aussi précise que possible concernant le temps passé dans les composants ODBC. Visual Studio Analyzer le suivi nécessite que toute source d’événement soit inscrite lorsque la source est configurée. Pour plus d’informations sur ce type de suivi, consultez la documentation de Visual Studio.
