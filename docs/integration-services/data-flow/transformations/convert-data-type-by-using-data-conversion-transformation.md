---
title: "Convertir des donn&#233;es en un type diff&#233;rent &#224; l&#39;aide de la transformation de conversion de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conversion des types de données [Integration Services]"
  - "transformation de conversion de données"
  - "types de données [Integration Services], conversion"
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# Convertir des donn&#233;es en un type diff&#233;rent &#224; l&#39;aide de la transformation de conversion de donn&#233;es
  Pour pouvoir ajouter et configurer une transformation de conversion de données, le package doit inclure au moins une tâche de flux de données et une source.  
  
### Pour convertir des données en un type différent  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de données** et, dans la **boîte à outils**, faites glisser la transformation de conversion de données sur l’aire de conception.  
  
4.  Connectez la transformation de conversion de données au flux de données en faisant glisser un connecteur à partir de la source ou de la transformation précédente vers la transformation de conversion de données.  
  
5.  Double-cliquez sur la transformation de conversion de données.  
  
6.  Dans la boîte de dialogue **Éditeur de transformation de conversion de données**, dans la table **Colonnes d’entrée disponibles**, cochez la case en regard des colonnes dont vous voulez convertir le type de données.  
  
    > [!NOTE]  
    >  Vous pouvez appliquer plusieurs conversions de données à une colonne d'entrée.  
  
7.  Si vous le souhaitez, modifiez les valeurs par défaut de la colonne **Alias de sortie**.  
  
8.  Dans la liste **Type de données**, sélectionnez le nouveau type de données de la colonne. Le type de données par défaut est celui de la colonne d'entrée.  
  
9. Si vous le souhaitez et selon le type de données sélectionné, mettez à jour les valeurs des colonnes **Longueur**, **Précision**, **Échelle** et **Page de codes**.  
  
10. Pour configurer la sortie d’erreur, cliquez sur **Configurer la sortie d’erreur**. Pour plus d’informations, consultez [Configurer une sortie d’erreur dans un composant de flux de données](../../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md).  
  
11. Cliquez sur **OK**.  
  
12. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## Voir aussi  
 [Transformation de conversion de données](../../../integration-services/data-flow/transformations/data-conversion-transformation.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Chemins d'accès d'Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Types de données d'Integration Services](../../../integration-services/data-flow/integration-services-data-types.md)   
 [tâche de flux de données](../../../integration-services/control-flow/data-flow-task.md)  
  
  