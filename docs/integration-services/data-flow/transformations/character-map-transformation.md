---
title: "Transformation de la table de caract&#232;res | Microsoft Docs"
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
  - "sql13.dts.designer.charactertrans.f1"
helpviewer_keywords: 
  - "mappages s'excluant mutuellement [Integration Services]"
  - "mappage de données [Integration Services]"
  - "fonctions de chaîne"
  - "transformation de la table de caractères [Integration Services]"
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Transformation de la table de caract&#232;res
  La transformation de la table de caractères applique des fonctions de chaîne, telles que la conversion de minuscules en majuscules, à des données de type caractère. Cette transformation fonctionne seulement sur les données de colonne de type de données chaîne.  
  
 La transformation de la table de caractères peut convertir les données de colonne sur place ou ajouter une colonne à la sortie de transformation et y insérer les données converties. Vous pouvez appliquer différents ensembles d'opérations de mappage à la même colonne d'entrée et placer les résultats dans des colonnes différentes. Par exemple, vous pouvez convertir la même colonne en majuscules et en minuscules, puis placer les résultats dans deux colonnes différentes.  
  
 Dans certaines circonstances, le mappage peut provoquer une troncation des données. Par exemple, la troncation peut se produire lorsque des caractères codés sur un octet sont mappés avec des caractères représentés sur plusieurs octets. La transformation de la table de caractères comprend une sortie d'erreur, qui permet de diriger les données tronquées vers une sortie distincte. Pour plus d’informations, consultez [Gestion des erreurs dans les données](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Cette transformation a une entrée, une sortie et une sortie d'erreur.  
  
## Opérations de mappage  
 Le tableau suivant décrit les opérations de mappage prises en charge par la transformation de la table de caractères.  
  
|Opération|Description|  
|---------------|-----------------|  
|Inversion d'octet|Inverse l'ordre des octets.|  
|Pleine chasse|Mappe des caractères à demi-chasse avec des caractères à pleine chasse.|  
|Demi-chasse|Mappe des caractères à pleine chasse avec des caractères à demi-chasse.|  
|Hiragana|Mappe des caractères katakana avec des caractères hiragana.|  
|Katakana|Mappe des caractères hiragana avec des caractères katakana.|  
|Casse linguistique|Applique une casse linguistique à la place des règles système. La casse linguistique fait référence aux fonctionnalités fournies par le mappage de casse simple API Win32 pour Unicode du turc et d'autres paramètres régionaux.|  
|Minuscules|Convertit des caractères en minuscules.|  
|Chinois simplifié|Mappe des caractères en chinois traditionnel avec des caractères en chinois simplifié.|  
|Chinois traditionnel|Mappe des caractères en chinois simplifié avec des caractères en chinois traditionnel.|  
|Majuscules|Convertit des caractères en majuscules.|  
  
## Opérations de mappage s'excluant mutuellement  
 Plusieurs opérations peuvent être réalisées dans une transformation. Toutefois, certaines opérations de mappage s'excluent mutuellement. Le tableau suivant décrit les restrictions applicables à l'utilisation de plusieurs opérations sur la même colonne. Les opérations dans les colonnes Opération A et Opération B s'excluent mutuellement.  
  
|Opération A|Opération B|  
|-----------------|-----------------|  
|Minuscules|Majuscules|  
|Hiragana|Katakana|  
|Demi-chasse|Pleine chasse|  
|Chinois traditionnel|Chinois simplifié|  
|Minuscules|Hiragana, katakana, demi-chasse, pleine chasse|  
|Majuscules|Hiragana, katakana, demi-chasse, pleine chasse|  
  
## Configuration de la transformation de la table de caractères  
 Vous pouvez configurer la transformation de la table de caractères comme suit :  
  
-   Spécifiez les colonnes à convertir.  
  
-   Spécifiez les opérations à appliquer à chaque colonne.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de la table des caractères** , consultez [Character Map Transformation Editor](../../../integration-services/data-flow/transformations/character-map-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d'informations sur la définition des propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   [Définir les propriétés d'un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  