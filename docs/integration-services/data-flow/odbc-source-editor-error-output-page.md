---
title: "&#201;diteur de source ODBC (page Sortie d&#39;erreur) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcsource.errorhandling.f1"
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# &#201;diteur de source ODBC (page Sortie d&#39;erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de source ODBC** pour sélectionner les options de gestion des erreurs.  
  
 Pour en savoir plus sur la source ODBC, consultez [CDC Source](../../integration-services/data-flow/cdc-source.md).  
  
## Liste des tâches  
 **Pour ouvrir l'Éditeur de source ODBC (page Sortie d'erreur)**  
  
-   Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] qui possède la source ODBC.  
  
-   Sous l’onglet **Flux de données**, double-cliquez sur la source ODBC.  
  
-   Dans l' **Éditeur de source ODBC**, cliquez sur **Sortie d'erreur**.  
  
## Options  
  
### Entrée/sortie  
 Affichez le nom de la source de données.  
  
### Colonne  
 Non utilisé.  
  
### Erreur  
 Sélectionnez la façon dont la source ODBC doit gérer les erreurs dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### Troncation  
 Sélectionnez la façon dont la source ODBC doit gérer la troncation dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### Description  
 Non utilisé.  
  
### Définir cette valeur sur les cellules sélectionnées  
 Sélectionnez la façon dont la source ODBC gère l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### Appliquer  
 Appliquez les options de gestion des erreurs aux cellules sélectionnées.  
  
## Options de gestion des erreurs  
 Vous pouvez utiliser les options suivantes pour configurer la façon dont la source ODBC gère les erreurs et les troncations.  
  
### Composant défaillant  
 La tâche de flux de données échoue lorsqu'une erreur ou une troncation a lieu. Il s'agit du comportement par défaut.  
  
### Ignorer l'échec  
 L'erreur ou la troncation est ignorée.  
  
### Rediriger le flux  
 La ligne qui provoque l'erreur ou la troncation est dirigée vers la sortie d'erreur de la source ODBC. Pour plus d'informations, consultez [ODBC Source](../../integration-services/data-flow/odbc-source.md).  
  
## Voir aussi  
 [Éditeur de source ODBC &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)   
 [Éditeur de source ODBC &#40;page Colonnes&#41;](../../integration-services/data-flow/odbc-source-editor-columns-page.md)  
  
  