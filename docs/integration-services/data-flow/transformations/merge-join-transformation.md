---
title: "Transformation de jointure de fusion | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.mergejointrans.f1"
helpviewer_keywords: 
  - "datasets [Integration Services]"
  - "transformation de jointure de fusion"
  - "jeux de données [Integration Services], jointure"
  - "jointure de datasets [Integration Services]"
  - "jointures [SQL Server], SSIS"
ms.assetid: cd8b0412-f83b-4bd2-b227-e53dcfd941a8
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 54
---
# Transformation de jointure de fusion
  La transformation de jointure de fusion fournit une sortie générée par la réunion, à l'aide d'une jointure FULL, LEFT ou INNER, de deux ensembles de données triés. Par exemple, vous pouvez utiliser une jointure LEFT pour associer une table comprenant des informations sur des produits à une table indiquant le pays ou la région dans lesquels un produit a été fabriqué. Le résultat est une table qui répertorie tous les produits et leur pays ou région d'origine.  
  
 Vous pouvez configurer la transformation de jointure de fusion comme suit :  
  
-   Indiquez si la jointure est une jointure FULL, LEFT ou INNER.  
  
-   Spécifiez les colonnes utilisées par la jointure.  
  
-   Indiquez si la transformation traite les valeurs NULL comme des valeurs égales.  
  
    > [!NOTE]  
    >  Si les valeurs NULL ne sont pas traitées comme des valeurs égales, la transformation les gère de la même manière que le moteur de base de données SQL Server.  
  
 Cette transformation a deux entrées et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## Spécifications relatives aux entrées  
 La transformation de jointure de fusion requiert des données triées pour ses entrées. Pour plus d’informations sur cette spécification importante, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
## Spécifications relatives à la jointure  
 La transformation de jointure de fusion requiert que les colonnes jointes aient des métadonnées correspondantes. Par exemple, vous ne pouvez pas joindre une colonne d'un type de données numérique à une colonne d'un type de données caractère. Si les données sont du type de données chaîne, la colonne de la deuxième entrée doit avoir une longueur inférieure ou égale à celle de la colonne de la première entrée avec laquelle elle est fusionnée.  
  
## Limitation du nombre de tampons  
 Vous n'avez plus à configurer la valeur de la propriété **MaxBuffersPerInput** car Microsoft a apporté des modifications qui réduisent le risque que la transformation de jointure de fusion consomme de la mémoire en excès. Ce problème s'est quelquefois produit lorsque plusieurs entrées de jointure de fusion produisaient des données à des taux irréguliers.  
  
## Tâches associées  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programme.  
  
 Pour plus d'informations sur la définition des propriétés de cette transformation, cliquez sur l'une des rubriques suivantes :  
  
-   [Étendre un dataset à l'aide de la transformation de jointure de fusion](../../../integration-services/data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)  
  
-   [Définir les propriétés d'un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## Voir aussi  
 [Éditeur de transformation de jointure de fusion](../../../integration-services/data-flow/transformations/merge-join-transformation-editor.md)   
 [Transformation de fusion](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Transformation d'union totale](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  