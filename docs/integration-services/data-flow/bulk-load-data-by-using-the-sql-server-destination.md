---
title: "Charger des donn&#233;es en masse &#224; l&#39;aide de la destination SQL&#160;Server | Microsoft Docs"
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
  - "Destination SQL Server"
  - "chargement de données"
  - "destinations [Integration Services], SQL Server"
  - "insertion de données"
  - "chargement en masse [Integration Services]"
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# Charger des donn&#233;es en masse &#224; l&#39;aide de la destination SQL&#160;Server
  Pour pouvoir ajouter et configurer une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le package doit inclure au moins une tâche de flux de données et une source de données.  
  
### Pour charger des données à l'aide d'une destination SQL Server  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l’aire de conception.  
  
4.  Connectez la destination à une source ou à une transformation précédente du flux de données en faisant glisser un connecteur vers la destination.  
  
5.  Double-cliquez sur la destination.  
  
6.  Dans la boîte de dialogue **Éditeur de destination SQL Server**, dans la page **Gestionnaire de connexions**, sélectionnez un gestionnaire de connexions OLE DB existant ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions. Pour plus d’informations, consultez [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
7.  Pour spécifier la table ou la vue dans laquelle charger les données, effectuez l'une des opérations suivantes :  
  
    -   Sélectionnez une table ou une vue existante.  
  
    -   Cliquez sur **Nouveau**, puis, dans la boîte de dialogue **Créer une table**, écrivez une instruction SQL qui crée une table ou une vue.  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] génère une instruction CREATE TABLE par défaut basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table**. Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
8.  Cliquez sur **Mappages** et mappez les colonnes de la liste **Colonnes d’entrée disponibles** aux colonnes de la liste **Colonnes de destination disponibles** en faisant glisser les colonnes d’une liste à l’autre.  
  
    > [!NOTE]  
    >  La destination mappe automatiquement les colonnes portant le même nom.  
  
9. Cliquez sur **Avancé** et définissez les options de chargement en masse : **Conserver l’identité**, **Conserver les valeurs NULL**, **Verrou de table**, **Vérifier les contraintes** et **Exécuter les déclencheurs**.  
  
     Si vous le souhaitez, indiquez la première et la dernière ligne d'entrée à insérer, le nombre maximal d'erreurs avant arrêt de l'opération d'insertion et les colonnes sur lesquelles l'insertion est triée.  
  
    > [!NOTE]  
    >  L'ordre de tri est déterminé par l'ordre dans lequel les colonnes apparaissent dans la liste.  
  
10. Cliquez sur **OK**.  
  
11. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## Voir aussi  
 [Destination SQL Server](../../integration-services/data-flow/sql-server-destination.md)   
 [Transformations Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Chemins d'accès d'Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [tâche de flux de données](../../integration-services/control-flow/data-flow-task.md)  
  
  