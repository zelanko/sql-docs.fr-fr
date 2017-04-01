---
title: "Options Demande de profil de statistiques de colonnes (t&#226;che de profilage des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éditeur de tâche de profilage de données"
ms.assetid: 87205984-507a-49f3-b27c-36a0075c234d
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Options Demande de profil de statistiques de colonnes (t&#226;che de profilage des donn&#233;es)
  Utilisez le volet **Propriétés de la demande** de la page **Demandes de profil** pour définir les options de la **Demande de profil de statistiques de colonnes** sélectionnée dans le volet Demandes. Un profil de statistiques de colonnes répertorie des statistiques, telles que l’écart minimal, maximal, moyen et type pour les colonnes numériques et l’écart minimal et maximal pour les colonnes **datetime**. Ce profil peut vous aider à identifier des problèmes dans vos données, tels que des dates non valides. Par exemple, vous profilez une colonne de dates historiques et découvrez une date maximum dont l'échéance est à venir.  
  
> [!NOTE]  
>  Les options décrites dans cette rubrique apparaissent sur la page **Demandes de profil** de l' **Éditeur de tâche de profilage de données**. Pour plus d’informations sur cette page de l’éditeur, consultez [Éditeur de tâche de profilage de données &#40;page Demandes de profil&#41;](../../integration-services/control-flow/data-profiling-task-editor-profile-requests-page.md).  
  
 Pour plus d’informations sur l’utilisation de la tâche de profilage des données, consultez [Configuration de la tâche de profilage des données](../../integration-services/control-flow/setup-of-the-data-profiling-task.md). Pour plus d’informations sur l’utilisation de la Visionneuse du profil des données pour analyser le résultat de la tâche de profilage de données, consultez [Visionneuse du profil des données](../../integration-services/control-flow/data-profile-viewer.md).  
  
## Options Propriétés de la demande  
 Pour une **demande de profil de statistiques de colonnes**, le volet **Propriétés de la demande** affiche les groupes d’options suivants :  
  
-   **Données**, qui incluent les options **TableOrView** et **Column**  
  
-   **Général**  
  
### Options de données  
 **ConnectionManager**  
 Sélectionnez le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] existant qui utilise le fournisseur de données .NET pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) pour établir la connexion à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contient la table ou la vue à profiler.  
  
 **TableOrView**  
 Sélectionnez la table ou la vue existante qui contient la colonne à profiler.  
  
 Pour plus d'informations, consultez la section « Options TableorView » dans cette rubrique.  
  
 **Colonne**  
 Sélectionnez la colonne existante à profiler. Sélectionnez **(\*)** pour profiler toutes les colonnes.  
  
 Pour plus d'informations, consultez la section « Options de colonne » dans cette rubrique.  
  
#### Options TableOrView  
 **Schéma**  
 Spécifie le schéma auquel la table sélectionnée appartient. Cette option est en lecture seule.  
  
 **Table**  
 Affiche le nom de la table sélectionnée. Cette option est en lecture seule.  
  
#### Options de colonne  
 **IsWildCard**  
 Spécifie si le caractère générique **(\*)** a été sélectionné. Cette option a la valeur **True** si vous avez sélectionné **(\*)** pour profiler toutes les colonnes. Sa valeur est **False** si vous avez sélectionné une colonne spécifique dont le profil doit être généré. Cette option est en lecture seule.  
  
 **ColumnName**  
 Affiche le nom de la colonne sélectionnée. Cette option est vide si vous avez sélectionné **(\*)** pour profiler toutes les colonnes. Cette option est en lecture seule.  
  
 **StringCompareOptions**  
 Cette option ne s'applique pas au profil de statistiques de colonnes.  
  
### Options générales  
 **RequestID**  
 Tapez un nom descriptif pour identifier cette demande de profil. En règle générale, il n'est pas nécessaire de modifier la valeur générée automatiquement.  
  
## Voir aussi  
 [Éditeur de tâche de profilage de données &#40;page Général&#41;](../../integration-services/control-flow/data-profiling-task-editor-general-page.md)   
 [Formulaire de profil rapide de table simple &#40;tâche de profilage des données&#41;](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)  
  
  