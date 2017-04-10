---
title: "&#201;diteur de destination ODBC (page Gestionnaire de connexions) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcdest.connection.f1"
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# &#201;diteur de destination ODBC (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination ODBC** pour sélectionner le gestionnaire de connexions ODBC de la destination. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
 Pour plus d'informations sur cette destination ODBC, consultez [ODBC Destination](../../integration-services/data-flow/odbc-destination.md).  
  
 **Pour ouvrir l'Éditeur de destination ODBC (page Gestionnaire de connexions)**  
  
## Liste des tâches  
  
-   Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] qui possède la destination ODBC.  
  
-   Sous l’onglet **Flux de données**, double-cliquez sur la destination ODBC.  
  
-   Dans l' **Éditeur de destination ODBC**, cliquez sur **Gestionnaire de connexions**.  
  
## Options  
  
### Gestionnaire de connexions  
 Sélectionnez un gestionnaire de connexions ODBC existant dans la liste ou cliquez sur Nouveau pour créer une nouvelle connexion. La connexion peut concerner n'importe quelle base de données prise en charge par ODBC.  
  
### Nouveau  
 Cliquez sur **Nouveau**. La boîte de dialogue **Configurer l'Éditeur du gestionnaire de connexions ODBC** s'ouvre et vous permet de créer un nouveau gestionnaire de connexions.  
  
### Mode d'accès aux données  
 Spécifiez la méthode de chargement des données dans la destination. Ces fonctions sont répertoriées dans le tableau suivant :  
  
|Option|Description|  
|------------|-----------------|  
|Nom de la table - Lot|Sélectionnez cette option pour configurer la destination ODBC en mode par lot. Lorsque vous sélectionnez cette option, les options suivantes sont disponibles :|  
||**Nom de la table ou de la vue**: sélectionnez une table ou une vue disponible dans la liste.<br /><br /> Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1000 tables, vous pouvez taper le début du nom d’une table ou utiliser le caractère générique (\*) pour entrer une partie du nom afin d’afficher la table ou les tables que vous souhaitez utiliser.<br /><br /> **Taille du lot**: entrez la taille du lot pour le chargement en bloc. Il s'agit du nombre de lignes chargées dans un même lot.|  
|Nom de la table - Ligne par ligne|Sélectionnez cette option pour configurer la destination ODBC de manière à insérer les lignes dans la table de destination une par une. Lorsque vous sélectionnez cette option, l'option suivante est disponible :|  
||**Nom de la table ou de la vue**: sélectionnez dans la liste une table ou une vue disponible dans la base de données.<br /><br /> Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1 000 tables, vous pouvez taper le début du nom d'une table ou utiliser le caractère générique (*) pour entrer une partie du nom afin d'afficher la table ou les tables que vous souhaitez utiliser.|  
  
### Aperçu  
 Cliquez sur **Aperçu** pour afficher jusqu'à 200 lignes de données pour la table sélectionnée.  
  
## Voir aussi  
 [Propriétés personnalisées des destinations ODBC](../../integration-services/data-flow/odbc-destination-custom-properties.md)   
 [Éditeur de destination ODBC &#40;page Mappages&#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)   
 [Éditeur de destination ODBC &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/odbc-destination-editor-error-output-page.md)  
  
  