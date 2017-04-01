---
title: "&#201;diteur de transformation de regroupement probable (onglet Avanc&#233;). | Microsoft Docs"
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
  - "sql13.dts.designer.fuzzygroupingtransformation.advanced.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de regroupement probable"
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# &#201;diteur de transformation de regroupement probable (onglet Avanc&#233;).
  Utilisez l'onglet **Avancé** de la boîte de dialogue **Éditeur de transformation de regroupement probable** pour spécifier les colonnes d'entrée et de sortie, définir des seuils de similarité et des séparateurs.  
  
> [!NOTE]  
>  Les propriétés **Exhaustive** et **MaxMemoryUsage** de la transformation de regroupement approximatif ne sont pas disponibles dans l' **Éditeur de transformation de regroupement approximatif**, mais elles peuvent être définies à l'aide de l' **Éditeur avancé**. Pour plus d'informations sur ces propriétés, consultez la section Transformation de regroupement approximatif dans [Transformation Custom Properties](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Pour en savoir plus sur la transformation de regroupement approximatif, consultez [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## Options  
 **Nom de la colonne clé d'entrée**  
 Spécifiez le nom d'une colonne de sortie qui contient l'identificateur unique de chaque ligne d'entée. La colonne **_key_in** a une valeur qui identifie chaque ligne de manière unique.  
  
 **Nom de la colonne clé de sortie**  
 Spécifiez le nom d'une colonne de sortie qui contient l'identificateur unique de la ligne canonique d'un groupe de lignes dupliquées. La colonne **_key_out** correspond à la valeur **_key_in** de la ligne de données canonique.  
  
 **Nom de colonne du score de similarité**  
 Spécifiez un nom qui contient le score de similarité. Le score de similarité est une valeur comprise entre 0 et 1 qui indique le niveau de similarité avec la ligne canonique. Plus le score se rapproche de 1, plus la ligne correspond à la ligne canonique.  
  
 **Seuil de similarité**  
 Définissez le seuil de similarité au moyen du curseur. Plus le seuil est proche de 1, plus la similarité entre les lignes est grande pour se qualifier comme lignes dupliquées. L'augmentation du seuil peut accélérer les recherches du fait que moins de candidats doivent être évalués.  
  
 **Séparateurs de jetons**  
 La transformation fournit un ensemble de séparateurs par défaut pour marquer des données, mais vous devez ajouter ou supprimer des séparateurs en modifiant la liste en fonction des besoins.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](../../../integration-services/data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  