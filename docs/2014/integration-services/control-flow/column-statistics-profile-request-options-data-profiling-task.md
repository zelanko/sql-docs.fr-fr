---
title: Options Demande de profil de statistiques de colonnes (tâche de profilage des données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 87205984-507a-49f3-b27c-36a0075c234d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e07bd6ead9ce0dfc20249f5db50a8b0b78ba242a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62832753"
---
# <a name="column-statistics-profile-request-options-data-profiling-task"></a>Options Demande de profil de statistiques de colonnes (tâche de profilage des données)
  Utilisez le volet **Propriétés de la demande** de la page **Demandes de profil** pour définir les options de la **Demande de profil de statistiques de colonnes** sélectionnée dans le volet Demandes. Un profil de statistiques de colonnes répertorie des statistiques, telles que l'écart minimal, maximal, moyen et type pour les colonnes numériques et l'écart minimal et maximal pour les colonnes `datetime`. Ce profil peut vous aider à identifier des problèmes dans vos données, tels que des dates non valides. Par exemple, vous profilez une colonne de dates historiques et découvrez une date maximum dont l'échéance est à venir.  
  
> [!NOTE]  
>  Les options décrites dans cette rubrique apparaissent sur la page **Demandes de profil** de l' **Éditeur de tâche de profilage de données**. Pour plus d’informations sur cette page de l’éditeur, consultez [Éditeur de tâche de profilage de données &#40;page Demandes de profil&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 Pour plus d’informations sur l’utilisation de la tâche de profilage des données, consultez [Configuration de la tâche de profilage des données](data-profiling-task.md). Pour plus d’informations sur l’utilisation de la visionneuse du profil des données pour analyser le résultat de la tâche de profilage des données, consultez [Visionneuse du profil des données](data-profile-viewer.md).  
  
## <a name="request-properties-options"></a>Options Propriétés de la demande  
 Pour une **demande de profil de statistiques de colonnes**, le volet **Propriétés de la demande** affiche les groupes d’options suivants :  
  
-   **Données**, qui incluent les options **TableOrView** et **Column**  
  
-   **Généralités**  
  
### <a name="data-options"></a>Options de données  
 **ConnectionManager**  
 Sélectionnez le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] existant qui utilise le fournisseur de données .NET pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) pour établir la connexion à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contient la table ou la vue à profiler.  
  
 **TableOrView**  
 Sélectionnez la table ou la vue existante qui contient la colonne à profiler.  
  
 Pour plus d'informations, consultez la section « Options TableorView » dans cette rubrique.  
  
 **Colonne**  
 Sélectionnez la colonne existante à profiler. Sélectionnez **(\*)** pour profiler toutes les colonnes.  
  
 Pour plus d'informations, consultez la section « Options de colonne » dans cette rubrique.  
  
#### <a name="tableorview-options"></a>Options TableOrView  
 **Schéma**  
 Spécifie le schéma auquel la table sélectionnée appartient. Cette option est en lecture seule.  
  
 **Table**  
 Affiche le nom de la table sélectionnée. Cette option est en lecture seule.  
  
#### <a name="column-options"></a>Options de colonne  
 **IsWildCard**  
 Indique si le caractère générique **(\*)** a été sélectionné. Cette option a la valeur **True** si vous avez sélectionné **(\*)** pour générer le profil de toutes les colonnes. Sa valeur est **False** si vous avez sélectionné une colonne spécifique dont le profil doit être généré. Cette option est en lecture seule.  
  
 **ColumnName**  
 Affiche le nom de la colonne sélectionnée. Cette option est vide si vous avez sélectionné **(\*)** pour générer le profil de toutes les colonnes. Cette option est en lecture seule.  
  
 **StringCompareOptions**  
 Cette option ne s'applique pas au profil de statistiques de colonnes.  
  
### <a name="general-options"></a>Options générales  
 **RequestID**  
 Tapez un nom descriptif pour identifier cette demande de profil. En règle générale, il n'est pas nécessaire de modifier la valeur générée automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de tâche de profilage de données &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)   
 [Formulaire de profil rapide de table simple &#40;tâche de profilage des données&#41;](single-table-quick-profile-form-data-profiling-task.md)  
  
  
