---
title: "&#201;diteur de source XML (page Gestionnaire de connexions) | Microsoft Docs"
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
  - "sql13.dts.designer.xmlsourceadapter.connectionmanager.f1"
helpviewer_keywords: 
  - "Éditeur de source XML"
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
caps.latest.revision: 20
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 20
---
# &#201;diteur de source XML (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de l' **Éditeur de source XML** pour spécifier un fichier XML et le schéma XSD qui transforme les données XML.  
  
 Pour plus d'informations sur la source XML, consultez [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## Options statiques  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Value|Description|  
|-----------|-----------------|  
|Emplacement du fichier XML|Récupère des données dans un fichier XML.|  
|Fichier XML à partir d'une variable|Spécifiez le nom de fichier XML dans une variable.<br /><br /> **Informations connexes** : [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md)|  
|Données XML à partir d'une variable|Récupère des données XML à partir d'une variable.|  
  
 **Utiliser le schéma inclus**  
 Indique si les données de la source XML contiennent le schéma XSD définissant et validant sa structure et ses données.  
  
 **Emplacement XSD**  
 Tapez le chemin et le nom de fichier du schéma XSD, ou recherchez le fichier en cliquant sur **Parcourir**.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir**, recherchez le fichier de schéma XSD.  
  
 **Créer XSD**  
 Utilisez la boîte de dialogue **Enregistrer sous** pour sélectionner l’emplacement du fichier de schéma XSD généré automatiquement. L'éditeur détermine le schéma en fonction de la structure des données XML.  
  
## Options dynamiques du mode d'accès aux données  
  
### Mode d'accès aux données = emplacement du fichier XML  
 **Emplacement XML**  
 Tapez le chemin et le nom du fichier de données XML, ou recherchez le fichier en cliquant sur **Parcourir**.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir**, recherchez le fichier de données XML.  
  
### Mode d'accès aux données = fichier XML à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable contenant le chemin d'accès et le nom du fichier XML.  
  
### Mode d'accès aux données = données XML à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable qui contient les données XML.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source XML &#40;page Colonnes&#41;](../../integration-services/data-flow/xml-source-editor-columns-page.md)   
 [Éditeur de source XML &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/xml-source-editor-error-output-page.md)   
 [Extraire des données à l'aide de la source XML](../../integration-services/data-flow/extract-data-by-using-the-xml-source.md)  
  
  