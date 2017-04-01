---
title: "&#201;diteur du gestionnaire de connexions de fichiers plats multiples (page G&#233;n&#233;ral) | Microsoft Docs"
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
  - "sql13.dts.designer.multifile.general.f1"
helpviewer_keywords: 
  - "Éditeur du gestionnaire de connexions de fichiers plats multiples"
ms.assetid: 00129d43-2772-413b-bdf8-ac5de81cf4a5
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# &#201;diteur du gestionnaire de connexions de fichiers plats multiples (page G&#233;n&#233;ral)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats multiples** pour sélectionner un groupe de fichiers ayant le même format de données et pour spécifier leur format de données. Une connexion de fichiers plats multiples permet à un package de se connecter à un groupe de fichiers texte ayant le même format.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers plats multiples, consultez [Multiple Flat Files Connection Manager](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md).  
  
## Options  
 **Nom du gestionnaire de connexions**  
 Spécifiez un nom unique pour la connexion de fichiers plats multiples dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Description**  
 Décrit la connexion. Il est recommandé d'indiquer ici l'usage auquel la connexion est destinée, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Noms de fichiers**  
 Tapez le chemin d'accès et les noms de fichiers à utiliser dans la connexion de fichiers plats multiples. Vous pouvez spécifier plusieurs fichiers à la fois en utilisant des caractères génériques (par exemple, C:\\*.txt) ou en utilisant la barre verticale (|) pour séparer plusieurs noms de fichiers. Tous les fichiers doivent avoir le même format de données.  
  
 **Parcourir**  
 Naviguez jusqu'aux noms de fichiers à utiliser dans la connexion de fichiers plats multiples. Vous pouvez sélectionner plusieurs fichiers. Tous les fichiers doivent avoir le même format de données.  
  
 **Paramètres régionaux**  
 Indiquez l'emplacement qui fournira les informations de classement et de conversion de la date et de l'heure.  
  
 **Unicode**  
 Indique s'il convient d'utiliser Unicode. L'utilisation d'Unicode vous empêche de spécifier une page de codes.  
  
 **Page de codes**  
 Spécifiez la page de codes pour du texte non-Unicode.  
  
 **Format**  
 Permet de préciser la mise en forme à utiliser : délimitée, à largeur fixe ou en drapeau à droite. Tous les fichiers doivent avoir le même format de données.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Délimité|Les colonnes sont séparées par les séparateurs spécifiés à la page **Colonnes** .|  
|Largeur fixe|Les colonnes ont une largeur fixe que vous spécifiez en faisant glisser les lignes des marqueurs dans la page **Colonnes** .|  
|En drapeau à droite|Dans les fichiers en drapeau à droite, toutes les colonnes ont une largeur fixe, sauf la dernière, qui est délimitée par le séparateur de lignes défini dans la page **Colonnes** .|  
  
 **Qualificateur de texte**  
 Spécifiez le qualificateur de texte à utiliser. Par exemple, vous pouvez spécifier de mettre le texte entre guillemets.  
  
 **Séparateur de lignes d'en-tête**  
 Choisissez dans la liste des séparateurs de lignes d'en-tête ou entrez le texte de séparation.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|La ligne d'en-tête est séparée par une combinaison retour chariot-saut de ligne.|  
|**{CR}**|La ligne d'en-tête est séparée par des retours chariot.|  
|**{LF}**|La ligne d'en-tête est séparée par des sauts de lignes.|  
|**Point-virgule {;}**|La ligne d'en-tête est séparée par des points-virgules.|  
|**Deux-points {:}**|La ligne d'en-tête est séparée par des deux-points.|  
|**Virgule {,}**|La ligne d'en-tête est séparée par des virgules.|  
|**Tabulation {t}**|La ligne d'en-tête est séparée par des tabulations.|  
|**Barre verticale {&#124;}**|La ligne d'en-tête est séparée par des barres verticales.|  
  
 **Lignes d'en-tête à ignorer**  
 Spécifiez le nombre de lignes d'en-tête à ignorer, le cas échéant.  
  
 **Noms de colonnes dans la première ligne de données**  
 Indique si des noms de colonne doivent être attendus ou fournis dans la première ligne de données.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Colonnes&#41;](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-columns-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Avancé&#41;](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-advanced-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Aperçu&#41;](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  