---
title: Filtrer les événements dans une trace
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 66780fe3a71f784679e80779985740a3d9069777
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307234"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>Filtrer des événements dans une trace (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Les filtres limitent les événements recueillis dans une trace. Si aucun filtre n'est défini, tous les événements des classes d'événements sélectionnées sont retournés dans le résultat de trace. Il n'est pas obligatoire de définir un filtre pour une trace. Toutefois, un filtre réduit la charge liée aux opérations de traçage.  
  
 Pour ajouter un filtre à une définition de trace, vous devez utiliser l’onglet **Sélection des événements** de la boîte de dialogue **Propriétés de la trace** ou **Propriétés du modèle de trace** .  
  
### <a name="to-filter-events-in-a-trace"></a>Pour filtrer les événements dans une trace  
  
1.  Dans la boîte de dialogue **Propriétés de la trace** ou **Propriétés du modèle de trace** , cliquez sur l’onglet **Sélection des événements** .  
  
     L’onglet **Sélection des événements** contient un contrôle de grille. Le contrôle de grille est une table qui contient chacune des classes d'événements traçables. La table contient une ligne par classe d'événements. Les classes d'événements peuvent différer légèrement, selon le type et la version du serveur auquel vous êtes connecté. Les classes d’événements sont identifiées dans la colonne **Événements** de la grille, et groupées par catégorie d’événement. Les autres colonnes répertorient les colonnes de données pouvant être retournées pour chaque classe d'événements.  
  
2.  Cliquez sur **Filtres de colonnes**.  
  
     La boîte de dialogue **Modifier le filtre** s’affiche. Cette **boîte de dialogue** contient une liste d’opérateurs de comparaison que vous pouvez utiliser pour filtrer les événements dans une trace.  
  
3.  Pour appliquer un filtre, cliquez sur l'opérateur de comparaison et tapez une valeur.  
  
4.  Cliquez sur **OK**.  
  
 **Considérations :**  
  
-   Si vous définissez un filtre sur les colonnes **StartTime** et **EndTime** de l’onglet Sélection des événements, vérifiez les éléments suivants :  
  
    -   La date est saisie au format suivant : `YYYY/MM/DD HH:mm:sec`.  
  
         OU  
  
    -   La case**Utiliser des paramètres régionaux pour afficher les valeurs de date et d’heure** est cochée dans la boîte de dialogue **Options générales** . Pour afficher la boîte de dialogue **Options générales**, dans le menu [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Outils**, cliquez sur **Option**.  
  
         - ET -  
  
    -   La date saisie se situe entre le 1er janvier 1753 et le 31 décembre 9999.  
  
-   Si le traçage des événements est réalisé avec l’utilitaire **osql** ou **sqlcmd** , il faut toujours ajouter **%** aux filtres de la colonne de données **TextData** .  
  
## <a name="see-also"></a> Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
