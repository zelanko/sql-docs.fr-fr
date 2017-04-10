---
title: "Ajouter une visionneuse de donn&#233;es &#224; un flux de donn&#233;es | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visionneuses de données [Integration Services]"
  - "flux de données [Integration Services], visionneuses de données"
  - "ajout de visionneuses de données"
ms.assetid: 5e573274-a170-4132-bfc8-a8ff3a8411e4
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Ajouter une visionneuse de donn&#233;es &#224; un flux de donn&#233;es
  Cette rubrique explique comment ajouter et configurer une visionneuse de données dans un flux de données. Une visionneuse de données affiche des données déplacées entre deux composants de flux de données Par exemple, une visionneuse de données peut afficher les données extraites d'une source de données avant qu'une transformation dans le flux de données modifie les données.  
  
 Un chemin d'accès connecte des composants d'un flux de données en reliant la sortie d'un composant à l'entrée d'un autre composant.  
  
 Avant que vous puissiez ajouter des visionneuses de données à un package, celui-ci doit inclure une tâche de flux de données et au moins deux composants de flux de données connectés.  
  
 Associe une visionneuse de données à une sortie d’erreur pour afficher la description de l’erreur et le nom de la colonne dans laquelle l’erreur s’est produite. Par défaut, la sortie d’erreur inclut uniquement des identificateurs numériques pour l’erreur et la colonne.  
  
### Pour ajouter une visionneuse de données à un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** , s'il n'est pas déjà sélectionné.  
  
4.  Cliquez sur la tâche de flux de données au flux de données de laquelle vous voulez joindre une visionneuse de données, puis cliquez sur l'onglet **Flux de données** .  
  
5.  Cliquez avec le bouton droit sur un chemin entre deux composants de flux de données, puis cliquez sur **Modifier**.  
  
6.  Dans la page **Général** , vous pouvez afficher et modifier les propriétés du chemin d'accès. Par exemple, dans la liste déroulante **PathAnnotation**, vous pouvez sélectionner l’annotation qui apparaît en regard du chemin.  
  
7.  Dans la page **Métadonnées** , vous pouvez afficher les métadonnées de la colonne et les copier dans le presse-papiers.  
  
8.  Dans la page **Visionneuse de données** , cliquez sur **Activer la visionneuse de données**.  
  
9. Dans la zone Colonnes à afficher, sélectionnez les colonnes à afficher dans la vue de source de données. Par défaut, toutes les colonnes disponibles sont sélectionnées et figurent dans la liste **Colonnes affichées** . Déplacez les colonnes que vous ne voulez pas utiliser dans la liste **Colonnes inutilisées** en les sélectionnant et en cliquant sur la flèche gauche.  
  
    > [!NOTE]  
    >  Dans la grille, les valeurs qui représentent les types de données DT_DATE, DT_DBTIME2, DT_FILETIME, DT_DBTIMESTAMP, DT_DBTIMESTAMP2 et DT_DBTIMESTAMPOFFSET apparaissent sous forme de chaînes au format ISO 8601 et un espace de séparation remplace le séparateur **T**. Les valeurs qui représentent les types de données DT_DATE et DT_FILETIME incluent sept chiffres pour les fractions de seconde. Étant donné que le type de données DT_FILETIME stocke uniquement trois chiffres pour les fractions de seconde, la grille affiche des zéros pour les quatre chiffres restants. Les valeurs qui représentent le type de données DT_DBTIMESTAMP incluent trois chiffres pour les fractions de seconde. Pour les valeurs qui représentent les types de données DT_DBTIME2, DT_DBTIMESTAMP2 et DT_DBTIMESTAMPOFFSET, le nombre de chiffres pour les fractions de seconde correspond à l'échelle spécifiée pour le type de données de la colonne. Pour plus d'informations sur les formats ISO 8601, consultez [Date and Time Formats](../Topic/Date%20and%20Time%20Formats.md). Pour plus d'informations sur les types de données, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
10. Cliquez sur **OK**.  
  
## Voir aussi  
 [Transformations Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Chemins d'accès d'Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Flux de données](../../integration-services/data-flow/data-flow.md)   
 [Débogage d'un flux de données](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
  