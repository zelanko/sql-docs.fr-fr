---
title: Évaluation des objets de base de données Access pour la Conversion (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- assessing SQL
- assessing syntax
- assessment reports
- creating assessment reports
- estimating migration effort
- reports
- SQL, assessing
- syntax, assessing
ms.assetid: 8b9e23d6-da62-437a-8c05-8ad2628b9441
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7d265ea1bd3b2461219858d39fd0b9164999cc30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722197"
---
# <a name="assessing-access-database-objects-for-conversion-accesstosql"></a>Évaluation des objets de base de données Access pour la Conversion (AccessToSQL)
Avant de charger des objets et de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vous devez déterminer la quantité de la migration sera réussie et la durée pendant laquelle la conversion peut prendre. SSMA peut créer un rapport d’évaluation qui affiche le pourcentage d’objets qui ont été correctement converties en valeurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de la syntaxe de SQL Azure et l’heure des estimations pour effectuer la migration. SSMA vous permet également d’afficher les problèmes spécifiques qui provoquait des échecs de conversion.  
  
## <a name="creating-assessment-reports"></a>Création de rapports d’évaluation  
Lorsqu’il crée un rapport d’évaluation, SSMA convertit les objets de base de données Access sélectionnés vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou syntaxe de SQL Azure, puis affiche les résultats.  
  
**Pour créer un rapport d’évaluation**  
  
1.  Dans l’Explorateur de métadonnées d’accès, sélectionnez la base de données ou les bases de données que vous souhaitez évaluer.  
  
2.  Pour omettre des objets individuels, désactivez les cases à cocher en regard des objets que vous ne souhaitez pas évaluer.  
  
3.  Avec le bouton droit **bases de données**, puis sélectionnez **créer un rapport**.  
  
    Vous pouvez également analyser les objets individuels en double-cliquant sur un objet, puis en sélectionnant **créer un rapport**.  
  
    SSMA affiche la progression dans la barre d’état en bas de la fenêtre. Si le volet de sortie est visible, vous verrez également des messages dans le volet de sortie.  
  
Une fois l’évaluation terminée, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Assistant de Migration pour l’accès : fenêtre de rapport d’évaluation s’affiche.  
  
## <a name="using-assessment-reports"></a>À l’aide de rapports d’évaluation  
La fenêtre de rapport d’évaluation contient trois volets : un Explorateur, un volet d’informations et un volet de message.  
  
-   Le volet Explorateur vous permet de parcourir les objets qui ont été évaluées. Vous pouvez cliquer sur les éléments dans ce volet pour Explorer les clés, les index et les tables individuelles.  
  
-   Le volet de détails affiche les statistiques de conversion de l’objet sélectionné.  
  
-   Le volet de message affiche les erreurs, avertissements et les messages d’information pour la conversion et estimations de temps pour effectuer la migration et les étapes de correction d’erreurs individuels.  
  
Vous devez corriger les erreurs avant de réexécuter le rapport d’évaluation ou convertir des schémas. Pour rechercher des erreurs, cliquez sur le **erreurs** situé dans le volet messages et développez chaque erreur pour afficher une liste d’objets où l’erreur s’est produite. Si vous cliquez sur un objet dans le volet messages, toutes les erreurs et avertissements pour cet objet seront affiche dans le volet détails.  
  
## <a name="next-step"></a>Étape suivante  
[Convertir des objets de base de données Access](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
