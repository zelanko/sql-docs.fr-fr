---
title: Définir les options de traçage (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307193"
---
# <a name="setting-tracing-options"></a>Définition des options de suivi
**L’onglet Tracing** de la boîte de dialogue **ODBC Data Source Administrator** vous permet de configurer la façon dont les appels de fonction ODBC sont tracés.  
  
## <a name="how-tracing-works"></a>Fonctionnement du traçage  
 Lorsque vous commencez à tracer à partir de **l’onglet Tracing,** le gestionnaire de pilote enregistre tous les appels de fonction ODBC pour toutes les applications exécutées ultérieurement. Les appels de fonction ODBC provenant d’applications qui sont en cours d’exécution avant le démarrage du traçage ne sont pas enregistrés. Les appels de fonction ODBC sont enregistrés dans un fichier journal que vous spécifiez.  
  
 Tracing s’arrête seulement après avoir **cliqué Stop Tracing Now**. N’oubliez pas que pendant que le traçage est allumé, le fichier journal continue d’augmenter et que cela affecte les performances de toutes vos applications ODBC.  
  
 Pour plus d’informations sur la recherche, voir [Tracing](../../odbc/reference/develop-app/tracing.md).  
  
### <a name="changes-in-odbc-tracing"></a>Changements dans le tracé de l’ODBC  
 Avant mdAC 2.7 SP2, le tracé de l’ODBC n’était autorisé qu’à se produire à l’échelle de la machine, dans lequel les traces captaient des détails exposés sur toutes les applications ODBC en cours d’exécution sous aucune identité. Il s’agissait notamment de retracer les activités liées à l’ODBC qui pourraient se produire pour les processus créés ou exécutés pour le compte d’autres comptes d’utilisateurs locaux et les principaux de sécurité intégrés tels que le Service local et le Service réseau.  
  
 Par défaut, le traçage ODBC utilise désormais le mode utilisateur. Toutefois, si vous êtes un administrateur local, vous pouvez toujours activer le traçage à l’échelle de la machine en utilisant l’administrateur de source de données ODBC.  
  
 Pour configurer le mode de traçage ODBC :  
  
1.  Si c’est nécessaire, connectez-vous à l’utilisation d’un compte qui a l’adhésion au groupe des administrateurs locaux.  
  
2.  À partir d’outils administratifs, ouvrez l’administrateur de source de données ODBC.  
  
3.  Cliquez sur l’onglet **Tracing.**  
  
4.  Configurez le mode de traçage à l’aide du **traçage Machine-Wide pour toutes les identités utilisateur** case de cocher:  
  
5.  Pour activer le traçage à l’échelle de la machine, sélectionnez la case à cocher.  
  
6.  Pour revenir au traçage par utilisateur, effacez la case à cocher.  
  
7.  Cliquez sur **Appliquer**.  
  
> [!NOTE]  
>  Si vous avez déjà commencé à tracer dans un mode, vous devez arrêter le traçage et passer à l’autre mode pour que le mode soit modifié avec succès.  
  
> [!IMPORTANT]  
>  Le traçage à l’échelle de la machine ne doit être activé que lorsqu’il est nécessaire; autrement, il devrait être éteint.  
  
## <a name="visual-studio-analyzer-tracing"></a>Traçage visual d’analyseur de studio  
  
> [!IMPORTANT]  
>  La prise en charge de Visual Studio Analyzer a été supprimée à partir de Windows 8 (Visual Studio Analyzer n’a été inclus que dans les anciennes versions de Visual Studio.). Pour un autre mécanisme de dépannage, utilisez le traçage BID.  
  
 Visual Studio® Analyzer Tracing fournit des informations sur les performances et le débogage sur la couche ODBC. Tous les événements sortants seront tirés à l’interface de haut niveau pour présenter une image aussi précise que possible concernant le temps passé dans les composants ODBC. Visual Studio Analyzer Tracing exige que toute source d’événements s’inscrive lorsque la source est configuré. Pour plus d’informations sur ce type de traçage, consultez la documentation Visual Studio.
