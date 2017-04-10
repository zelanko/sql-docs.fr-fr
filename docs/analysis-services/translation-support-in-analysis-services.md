---
title: "Prise en charge des traductions dans Analysis&#160;Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Intelligence Development Studio, traductions [Analysis Services]"
  - "traductions [Analysis Services], à propos des traductions"
  - "traductions d'objets [Analysis Services]"
  - "identificateurs de langue [Analysis Services]"
  - "traductions d'attributs [Analysis Services]"
  - "traductions [Analysis Services]"
ms.assetid: 018471e0-3c82-49ec-aa16-467fb58a6d5f
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Prise en charge des traductions dans Analysis&#160;Services
  Dans des modèles de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous pouvez incorporer plusieurs traductions d’une légende ou d’une description pour fournir des chaînes spécifiques aux paramètres régionaux en fonction de l’identificateur LCID. Dans le cas des modèles multidimensionnels, vous pouvez ajouter des traductions pour le nom de la base de données, les objets cube et les objets de dimension de base de données. Pour les modèles tabulaires, vous pouvez traduire les descriptions et légendes des tables et des colonnes.  
  
 La définition d’une traduction crée les métadonnées et la légende traduite à l’intérieur du modèle. Cependant, pour restituer des chaînes localisées dans une application cliente, vous devez définir la propriété **Language** sur l’objet ou passer un paramètre **Culture** ou **Locale Identifier** sur la chaîne de connexion (par exemple, en définissant `LocaleIdentifier=1036` afin de retourner des chaînes en français).  
  
 Utilisez **Locale Identifier** si vous souhaitez prendre en charge plusieurs traductions simultanées du même objet dans différentes langues. Définir la propriété **Language** fonctionne, mais cela affecte aussi le traitement et les requêtes, ce qui pourrait avoir des conséquences inattendues. Définir **Locale Identifier** constitue le meilleur choix, car il est utilisé uniquement pour retourner des chaînes traduites.  
  
 Une traduction est composée d'un identificateur de paramètres régionaux (LCID), d'une légende traduite pour l'objet (par exemple le nom de la dimension ou de l'attribut) et éventuellement d'une liaison à une colonne qui fournit des valeurs de données dans la langue cible. Vous pouvez avoir plusieurs traductions, mais vous ne pouvez en utiliser qu'une seule pour une connexion donnée. Il n'existe aucune limite théorique quant au nombre de traductions que vous pouvez incorporer dans le modèle, mais chaque traduction ajoute une complexité au test et toutes les traductions doivent partager le même classement. Vous devez donc garder ces contraintes naturelles à l'esprit lors de la conception de votre solution.  
  
> [!TIP]  
>  Vous pouvez utiliser des applications clientes telles qu'Excel, Management Studio et SQL Server Profiler pour retourner des chaînes traduites. Pour plus d’informations, consultez [Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md).  
  
## Comment ajouter des métadonnées traduites à un modèle dans Analysis Services  
 Pour obtenir des instructions pas à pas, cliquez sur les liens suivants :  
  
-   [Traductions dans les modèles tabulaires &#40;Analysis Services&#41;](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [Traductions dans les modèles multidimensionnels &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## Voir aussi  
 [Scénarios de globalisation pour Analysis Services](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Langues et classements &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md)   
 [Définir ou modifier le classement des colonnes](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  