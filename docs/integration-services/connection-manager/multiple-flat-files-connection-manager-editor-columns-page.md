---
title: "&#201;diteur du gestionnaire de connexions de fichiers plats multiples (page Colonnes) | Microsoft Docs"
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
  - "sql13.dts.designer.multifile.columns.f1"
helpviewer_keywords: 
  - "Éditeur du gestionnaire de connexions de fichiers plats multiples"
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# &#201;diteur du gestionnaire de connexions de fichiers plats multiples (page Colonnes)
  Utilisez le nœud **Colonnes** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats multiples** pour spécifier les informations de ligne et de colonne et afficher un aperçu du premier fichier sélectionné.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers plats multiples, consultez [Multiple Flat Files Connection Manager](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md).  
  
## Options statiques  
 **Nom du gestionnaire de connexions**  
 Spécifiez un nom unique pour la connexion de fichiers plats multiples dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Description**  
 Décrit la connexion. Il est recommandé d'indiquer ici l'usage auquel la connexion est destinée, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
## Options dynamiques de format de fichier plat  
  
### Format = Délimité  
 **Séparateur de lignes**  
 Effectuez une sélection dans la liste des séparateurs de lignes disponibles ou entrez le texte du séparateur.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les lignes sont séparées par une combinaison de retour chariot/saut de ligne.|  
|**{CR}**|Les lignes sont séparées par un retour chariot.|  
|**{LF}**|Les lignes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les lignes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les lignes sont séparées par un deux-points.|  
|**Virgule {,}**|Les lignes sont séparées par une virgule.|  
|**Tabulation {t}**|Les lignes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les lignes sont séparées par une barre verticale.|  
  
 **Délimiteur de colonne**  
 Effectuez une sélection dans la liste des séparateurs de colonnes disponibles ou entrez le texte du séparateur.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les colonnes sont délimitées par une combinaison retour chariot-saut de ligne.|  
|**{CR}**|Les colonnes sont séparées par un retour chariot.|  
|**{LF}**|Les colonnes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les colonnes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les colonnes sont séparées par un deux-points.|  
|**Virgule {,}**|Les colonnes sont séparées par une virgule.|  
|**Tabulation {t}**|Les colonnes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les colonnes sont séparées par une barre verticale.|  
  
 **Réinitialiser les colonnes**  
 Cliquez sur **Réinitialiser les colonnes** pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
### Format = Largeur fixe  
 **Police**  
 Sélectionnez la police d'affichage de l'aperçu des données.  
  
 **Colonnes de données sources**  
 Ajustez la largeur de la ligne en faisant glisser le marqueur de ligne vertical, et celle des colonnes en cliquant sur la règle en haut de la fenêtre d'aperçu.  
  
 **Largeur de ligne**  
 Spécifiez la largeur de la ligne avant d'ajouter des séparateurs pour des colonnes distinctes. Vous pouvez également faire glisser la ligne verticale dans la fenêtre d'aperçu pour marquer la fin de la ligne. La valeur de la largeur de ligne est automatiquement mise à jour.  
  
 **Réinitialiser les colonnes**  
 Cliquez sur **Réinitialiser les colonnes** pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
### Format = En drapeau à droite  
  
> [!NOTE]  
>  Les fichiers en drapeau à droite sont ceux dans lesquels chaque colonne possède une largeur fixe, à l'exception de la dernière. Un séparateur de lignes s'applique.  
  
 **Police**  
 Sélectionnez la police d'affichage de l'aperçu des données.  
  
 **Colonnes de données sources**  
 Ajustez la largeur de la ligne en faisant glisser le marqueur de ligne vertical, et celle des colonnes en cliquant sur la règle en haut de la fenêtre d'aperçu.  
  
 **Séparateur de lignes**  
 Effectuez une sélection dans la liste des séparateurs de lignes disponibles ou entrez le texte du séparateur.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les lignes sont séparées par une combinaison de retour chariot/saut de ligne.|  
|**{CR}**|Les lignes sont séparées par un retour chariot.|  
|**{LF}**|Les lignes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les lignes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les lignes sont séparées par un deux-points.|  
|**Virgule {,}**|Les lignes sont séparées par une virgule.|  
|**Tabulation {t}**|Les lignes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les lignes sont séparées par une barre verticale.|  
  
 **Réinitialiser les colonnes**  
 Cliquez sur **Réinitialiser les colonnes** pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Général&#41;](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-general-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Avancé&#41;](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-advanced-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Aperçu&#41;](../../integration-services/connection-manager/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  