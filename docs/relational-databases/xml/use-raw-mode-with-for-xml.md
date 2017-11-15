---
title: Utiliser le mode RAW avec FOR XML | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
caps.latest.revision: "45"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8e21387a6b1b3b89bd06fc191a32024d73adf3ff
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="use-raw-mode-with-for-xml"></a>Utiliser le mode RAW avec FOR XML
  Le mode RAW transforme chaque ligne du jeu de résultats de la requête en un élément XML contenant l’identificateur générique \<row> ou le nom d’élément éventuellement fourni. Par défaut, chaque valeur de colonne dans l’ensemble de lignes qui n’est pas NULL est mappée à un attribut de l’élément \<row>. Si la directive ELEMENTS est ajoutée à la clause FOR XML, chaque valeur de colonne est mappée à un sous-élément de l’élément \<row>. Avec la directive ELEMENTS, vous pouvez éventuellement spécifier l'option XSINIL pour mapper les valeurs de colonnes NULL dans le jeu de résultats à un élément qui possède l'attribut xsi:nil=`"`true`"`.  
  
 Vous pouvez demander un schéma pour les données XML résultantes. Spécifier l'option XMLDATA permet de retourner un schéma XDR en ligne. Spécifier l'option XMLSCHEMA permet de retourner un schéma XSD en ligne. Le schéma apparaît au début des données. Dans le résultat, la référence à l'espace de noms du schéma est répétée pour chaque élément de niveau supérieur.  
  
 L'option BINARY BASE64 doit être spécifiée dans la clause FOR XML pour retourner les données binaires dans un format encodé en base 64. En mode RAW, la récupération de données binaires sans spécification de l'option BINARY BASE64 génère une erreur.  
  
## <a name="in-this-section"></a>Dans cette section  
 Cette section contient les exemples suivants :  
  
-   [Exemple : récupération des informations de modèle de produit au format XML](../../relational-databases/xml/example-retrieving-product-model-information-as-xml.md)  
  
-   [Exemple : spécification de XSINIL avec la directive ELEMENTS](../../relational-databases/xml/example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [Exemple : demande de schémas comme résultats à l'aide des options XMLDATA et XMLSCHEMA](../../relational-databases/xml/example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [Exemple : extraction de données binaires](../../relational-databases/xml/example-retrieving-binary-data.md)  
  
-   [Exemple : Renommage de l’élément &#60;row&#62;](../../relational-databases/xml/example-renaming-the-row-element.md)  
  
-   [Exemple : spécification d'un élément racine pour les données XML générées par FOR XML](../../relational-databases/xml/example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [Exemple: interrogation de colonnes de type XML](../../relational-databases/xml/example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [UTiliser le mode AUTO avec FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)   
 [Utiliser le mode EXPLICIT avec FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)   
 [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML &#40;SQL Server&#41;](../../relational-databases/xml/for-xml-sql-server.md)  
  
  
