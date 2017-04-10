---
title: "&#201;diteur de destination ODBC (page Sortie d&#39;erreur) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcdest.errorhandling.f1"
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# &#201;diteur de destination ODBC (page Sortie d&#39;erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de destination ODBC** pour sélectionner les options de gestion des erreurs.  
  
 Pour en savoir plus sur la destination ODBC, consultez [ODBC Destination](../../integration-services/data-flow/odbc-destination.md).  
  
 **Pour ouvrir l'Éditeur de destination ODBC (page Sortie d'erreur)**  
  
## Liste des tâches  
  
-   Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] qui possède la destination ODBC.  
  
-   Sous l’onglet **Flux de données**, double-cliquez sur la destination ODBC.  
  
-   Dans l' **Éditeur de destination ODBC**, cliquez sur **Sortie d'erreur**.  
  
## Options  
  
### Entrée/sortie  
 Affichez le nom de la source de données.  
  
### Colonne  
 Non utilisé.  
  
### Erreur  
 Sélectionnez la façon dont la destination ODBC doit gérer les erreurs dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### Troncation  
 Sélectionnez la façon dont la destination ODBC doit gérer la troncation dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### Description  
 Affichez la description d'une erreur.  
  
### Définir cette valeur sur les cellules sélectionnées  
 Sélectionnez la façon dont la destination ODBC gère l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### Appliquer  
 Appliquez les options de gestion des erreurs aux cellules sélectionnées.  
  
## Options de gestion des erreurs  
 Vous pouvez utiliser les options suivantes pour configurer la façon dont la destination ODBC gère les erreurs et les troncations.  
  
### Composant défaillant  
 La tâche de flux de données échoue lorsqu'une erreur ou une troncation a lieu. Il s'agit du comportement par défaut.  
  
### Ignorer l'échec  
 L'erreur ou la troncation est ignorée.  
  
### Rediriger le flux  
 La ligne qui provoque l'erreur ou la troncation est dirigée vers la sortie d'erreur de la destination ODBC. Pour plus d'informations, consultez Destination ODBC.  
  
## Voir aussi  
 [Éditeur de destination ODBC &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/odbc-destination-editor-connection-manager-page.md)   
 [Éditeur de destination ODBC &#40;page Mappages&#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)  
  
  