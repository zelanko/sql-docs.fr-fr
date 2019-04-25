---
title: Éditeur du Gestionnaire de connexions de fichier (Page Général) plats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.general.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 77296024-5c1a-4f6a-9665-0b50d45d744c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8282cf7060f106798f2fa482f474bc5e364492ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768315"
---
# <a name="flat-file-connection-manager-editor-general-page"></a>Éditeur du gestionnaire de connexions de fichiers plats (page Général)
  La page **Général** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** vous permet de sélectionner un format de fichier et de données. Une connexion de fichier plat permet à un package de se connecter à un fichier texte.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers plats, consultez [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Options  
 **Nom du gestionnaire de connexions**  
 Permet de fournir un nom unique pour la connexion de fichier plat dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrit la connexion. Il est recommandé d'indiquer ici l'usage auquel la connexion est destinée, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Nom de fichier**  
 Tapez le chemin d'accès et le nom de fichier à utiliser dans la connexion de fichier plat.  
  
 **Parcourir**  
 Recherchez le nom de fichier à utiliser dans la connexion de fichier plat.  
  
 **Paramètres régionaux**  
 Spécifiez les paramètres régionaux pour fournir les informations spécifiques à la langue relatives à l'ordre et aux formats de date et d'heure.  
  
 **Unicode**  
 Indique s'il convient d'utiliser Unicode. Si vous utilisez Unicode, vous ne pouvez pas spécifier de page de codes.  
  
 **Page de codes**  
 Spécifiez la page de codes pour du texte non-Unicode.  
  
 **Format**  
 Indique si le fichier utilise une mise en forme délimitée, à largeur fixe ou en drapeau à droite.  
  
|Value|Description|  
|-----------|-----------------|  
|Délimité|Les colonnes sont séparées par les séparateurs spécifiés à la page **Colonnes** .|  
|Largeur fixe|Les colonnes ont une largeur fixe.|  
|En drapeau à droite|Les fichiers en drapeau à droite sont des fichiers dans lesquels chaque colonne a une largeur fixe, à l'exception de la dernière colonne. Un séparateur de lignes s'applique.|  
  
 **Qualificateur de texte**  
 Spécifiez le qualificateur de texte à utiliser. Par exemple, vous pouvez spécifier que les champs de texte soient placés entre guillemets.  
  
> [!NOTE]  
>  Après avoir sélectionné un identificateur de texte, vous ne pouvez pas sélectionner de nouveau l’option **Aucun** . Tapez **Aucun** pour désélectionner l’identificateur de texte.  
  
 **Séparateur de lignes d'en-tête**  
 Choisissez dans la liste des séparateurs de lignes d'en-tête ou entrez le texte de séparation.  
  
|Value|Description|  
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
 Spécifiez le nombre de lignes d'en-tête ou de lignes de données initiales à ignorer, le cas échéant.  
  
 **Noms de colonnes dans la première ligne de données**  
 Indique si des noms de colonne doivent être attendus ou fournis dans la première ligne de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
