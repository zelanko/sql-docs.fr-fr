---
title: Éditeur du Gestionnaire de connexions (Page colonnes) de fichiers plats multiples | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.multifile.columns.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 47927f2a39679c715553ff8c53390ef631661e90
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142303"
---
# <a name="multiple-flat-files-connection-manager-editor-columns-page"></a>Éditeur du gestionnaire de connexions de fichiers plats multiples (page Colonnes)
  Utilisez le nœud **Colonnes** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats multiples** pour spécifier les informations de ligne et de colonne et afficher un aperçu du premier fichier sélectionné.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers plats multiples, consultez [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
## <a name="static-options"></a>Options statiques  
 **Nom du gestionnaire de connexions**  
 Spécifiez un nom unique pour la connexion de fichiers plats multiples dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrit la connexion. Il est recommandé d'indiquer ici l'usage auquel la connexion est destinée, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
## <a name="flat-file-format-dynamic-options"></a>Options dynamiques de format de fichier plat  
  
### <a name="format--delimited"></a>Format = Délimité  
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
 Cliquez sur **Réinitialiser les colonnes**pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
### <a name="format--fixed-width"></a>Format = Largeur fixe  
 **Police**  
 Sélectionnez la police d'affichage de l'aperçu des données.  
  
 **Colonnes de données sources**  
 Ajustez la largeur de la ligne en faisant glisser le marqueur de ligne vertical, et celle des colonnes en cliquant sur la règle en haut de la fenêtre d'aperçu.  
  
 **Largeur de ligne**  
 Spécifiez la largeur de la ligne avant d'ajouter des séparateurs pour des colonnes distinctes. Vous pouvez également faire glisser la ligne verticale dans la fenêtre d'aperçu pour marquer la fin de la ligne. La valeur de la largeur de ligne est automatiquement mise à jour.  
  
 **Réinitialiser les colonnes**  
 Cliquez sur **Réinitialiser les colonnes**pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
### <a name="format--ragged-right"></a>Format = En drapeau à droite  
  
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
 Cliquez sur **Réinitialiser les colonnes**pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;Page avancé&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)   
 [Éditeur du Gestionnaire de connexions de fichiers plats multiples &#40;afficher un aperçu de la Page&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  