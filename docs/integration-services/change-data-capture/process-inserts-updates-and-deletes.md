---
title: "Traiter les insertions, les mises &#224; jour et les suppressions | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "chargement incrémentiel [Integration Services], traitement de données"
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Traiter les insertions, les mises &#224; jour et les suppressions
  Dans le flux de données d'un package Integration Services qui effectue un chargement incrémentiel des données modifiées, la deuxième tâche consiste à séparer les insertions, les mises à jour et les suppressions. Ensuite, vous pouvez utiliser des commandes appropriées pour les appliquer à la destination.  
  
> [!NOTE]  
>  La première tâche pour concevoir le flux de données d'un package qui effectue un chargement incrémentiel des données modifiées consiste à configurer le composant source qui exécute la requête qui récupère les données modifiées. Pour plus d’informations sur ce composant, consultez [Récupérer et comprendre les données modifiées](../../integration-services/change-data-capture/retrieve-and-understand-the-change-data.md). Pour obtenir une description du processus d’ensemble de la création d’un package qui effectue un chargement incrémentiel des données modifiées, consultez [Capture de données modifiées &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## Association de valeurs conviviales pour séparer des insertions, des mises à jour et des suppressions  
 Dans l’exemple de requête qui récupère les données modifiées, la fonction **cdc.fn_cdc_get_net_changes_<capture_instance>** retourne uniquement la colonne de métadonnées nommée **__$operation**. Cette colonne de métadonnées contient une valeur ordinale qui indique l'opération ayant entraîné la modification.  
  
> [!NOTE]  
>  Pour plus d’informations sur la requête qui utilise la fonction **cdc.fn_cdc_get_net_changes_<capture_instance>**, consultez [Créer la fonction de récupération des données modifiées](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md).  
  
 La mise en correspondance d'une valeur ordinale à son opération associée n'est pas aussi facile que d'utiliser un mnémonique de l'opération. Par exemple, 'D' peut facilement représenter une opération de suppression (Delete) et 'I' une opération d'insertion. L’exemple de requête créé dans la rubrique [Création de la fonction de récupération des données modifiées](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md) effectue cette conversion d’une valeur ordinale en valeur de chaîne conviviale qui est retournée dans une nouvelle colonne. Le segment de code suivant illustre cette conversion :  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## Configuration d'une transformation de fractionnement conditionnel pour diriger des insertions, des mises à jour et des suppressions  
 Pour diriger des lignes de données modifiées vers l'une des trois sorties, la transformation de fractionnement conditionnel est idéale. La transformation vérifie simplement la valeur de la colonne **CDC_OPERATION** dans chaque ligne et détermine si cette modification est une insertion, une mise à jour ou une suppression.  
  
> [!NOTE]  
>  La colonne CDC_OPERATION contient une valeur de chaîne conviviale dérivée de la valeur numérique dans la colonne **__$operation**.  
  
#### Pour fractionner des insertions, des mises à jour et des suppressions à des fins de traitement à l'aide d'une transformation de fractionnement conditionnel  
  
1.  Sous l’onglet **Flux de données**, ajoutez une transformation de fractionnement conditionnel.  
  
2.  Connectez la sortie de la source OLE DB à la transformation de fractionnement conditionnel.  
  
3.  Dans **Éditeur de transformation de fractionnement conditionnel**, dans le volet inférieur de l’éditeur, entrez les trois lignes suivantes pour désigner les trois sorties.  
  
    1.  Entrez une ligne avec la condition `CDC_OPERATION == "I"` pour diriger des lignes insérées vers la sortie pour les insertions.  
  
    2.  Entrez une ligne avec la condition `CDC_OPERATION == "U"` pour diriger des lignes mises à jours vers la sortie pour des mises à jours.  
  
    3.  Entrez une ligne avec la condition `CDC_OPERATION == "D"` pour diriger des lignes supprimées vers la sortie pour des suppressions.  
  
## Étape suivante  
 Après avoir fractionné les lignes à des fins de traitement, l'étape suivante consiste à appliquer les modifications à la destination.  
  
 **Rubrique suivante : ** [Appliquer les modifications à la destination](../../integration-services/change-data-capture/apply-the-changes-to-the-destination.md)  
  
## Voir aussi  
 [Transformation de fractionnement conditionnel](../../integration-services/data-flow/transformations/conditional-split-transformation.md)   
 [Fractionner un dataset à l'aide de la transformation de fractionnement conditionnel](../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  