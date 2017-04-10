---
title: "&#201;diteur de source CDC (page Sortie d&#39;erreur) | Microsoft Docs"
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
  - "sql13.ssis.designer.cdcsource.errorhandling.f1"
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# &#201;diteur de source CDC (page Sortie d&#39;erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de source CDC** pour sélectionner les options de gestion des erreurs.  
  
 Pour en savoir plus sur la source CDC, consultez [CDC Source](../../integration-services/data-flow/cdc-source.md).  
  
## Liste des tâches  
 **Pour ouvrir l'Éditeur de source CDC (page Sortie d'erreur)**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] qui possède la source CDC.  
  
2.  Sous l’onglet **Flux de données**, double-cliquez sur la source CDC.  
  
3.  Dans l' **Éditeur de source CDC**, cliquez sur **Sortie d'erreur**.  
  
## Options  
 **Entrée/sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Affichez les colonnes externes (sources) que vous avez sélectionnées dans la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source CDC**.  
  
 **Erreur**  
 Sélectionnez la façon dont la source CDC doit gérer les erreurs dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Troncation**  
 Sélectionnez la façon dont la source CDC doit gérer la troncation dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Non utilisé.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Sélectionnez la façon dont la source CDC gère l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez les options de gestion des erreurs aux cellules sélectionnées.  
  
## Options de gestion des erreurs  
 Vous pouvez utiliser les options suivantes pour configurer la façon dont la source CDC gère les erreurs et les troncations.  
  
 **Composant défaillant**  
 La tâche de flux de données échoue lorsqu'une erreur ou une troncation a lieu. Il s'agit du comportement par défaut.  
  
 **Ignorer l'échec**  
 L'erreur ou la troncation est ignorée et la ligne de données est dirigée vers la sortie de la source CDC.  
  
 **Rediriger le flux**  
 La ligne de données qui présente l'erreur ou la troncation est dirigée vers la sortie d'erreur de la source CDC. Dans ce cas, la gestion des erreurs de la source CDC est utilisée. Pour plus d'informations, consultez [CDC Source](../../integration-services/data-flow/cdc-source.md).  
  
## Voir aussi  
 [Éditeur de source CDC &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [Éditeur de source CDC &#40;page Colonnes&#41;](../../integration-services/data-flow/cdc-source-editor-columns-page.md)  
  
  